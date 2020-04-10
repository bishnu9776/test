node{
	stage('Checkout'){
		cleanWs()

		// Method 1: Create directories and use them to clone individual modules but this requires admin level permissions and is not secured
		echo "Creating Directories for X Project"

		// Give all the repo names in place of one, two, three
        new File('one').mkdir()
        new File('two').mkdir()
        new File('three').mkdir()

		// clone each repo make sure you change the branch and repo here and the folder name which you created above,
    	dir ('one') {
    	    git branch: "release-2.10.0", changelog: false, poll: false, url: 'https://github.com/MasterAlt/sunbird-devops.git'
    	}

    	dir ('two') {
    	    git branch: "release-2.7.0", changelog: false, poll: false, url: 'https://github.com/MasterAlt/sunbird-data-pipeline.git'
    	}
    	dir ('three') {
    	    git branch: "master", changelog: false, poll: false, url: 'https://github.com/smyaltamash/king.git'
    	}
		
		// Method 2: Use checkout module to clone into specific folder and branch also use the private repo authentication
		checkout([$class: 'GitSCM', branches: [[name: '*/release-2.10.0']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'private']], userRemoteConfigs: [[credentialsId: 'privateCredentialID', url: 'https://github.com/ekstep/sunbird-devops']]])
	}

	// Have the Build 
	stage('Build'){
		echo "Run the maven commands"
	}

	// Send the sonar reports
	stage('Sonar'){
		echo "Send the sonar reports"
	}
}
//this will checkout code according to their folder
/*
node{
stage('Checkout'){
// Repo 1
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'eventmodule']], userRemoteConfigs: [[credentialsId: 'GitCred', url: 'https://git.cropin.in/cropinV2/smartfarm/farm/com.cropin.smartfarm.farm.eventmodule.git']]])

// Repo 2
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'tenantmodule']], userRemoteConfigs: [[credentialsId: 'GitCred', url: 'https://git.cropin.in/cropinV2/smartfarm/farm/com.cropin.smartfarm.farm.tenantmodule.git']]])

// Repo 3
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'services']], userRemoteConfigs: [[credentialsId: 'GitCred', url: 'https://git.cropin.in/cropinV2/smartfarm/farm/com.cropin.smartfarm.farm.services.git']]])
}

// Have the Build
stage('Build'){
echo "Run the maven commands"
dir('eventmodule')
			{ sh "mvn clean install -Dmaven.test.skip=true"
			}
dir ('tenantmodule')
			{ sh "mvn clean install -Dmaven.test.skip=true"
			}
dir('services')
			{ sh "mvn clean install -Dmaven.test.skip=true"
			}}

// Send the sonar reports
stage('Sonar'){
echo "Send the sonar reports"
dir('eventmodule')
			{ sh "mvn sonar:sonar"
			}
dir ('tenantmodule')
			{ sh "mvn sonar:sonar"
			}
dir('services')
			{ sh "mvn sonar:sonar "
			}
		}
		}
*/
