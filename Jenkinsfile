#!groovy
node('slave1') {
   try {
         stage ('Checkout'){
            checkout scm      
         }
         stage ('Build Gradle'){
           def gradleHome = tool 'gradle4'
           sh "${gradleHome}/bin/gradle build"
         }
   	} 
   catch (ex) {
		echo "Some failed"
	}
   stage ('post'){
        if ( currentBuild.result == 'SUCCESS') {
          addBadge(text: 'Build Success')
        }
        if (currentBuild.result == 'FAILURE') {
          addBadge(text: 'Build Faiure')
         }
   }
}
