#!groovy
pipeline{
    agent {
    label 'slave1'
    }
       tools {
           gradle 'gradle4'
        }
   stages {
       try {
         stage ('Checkout'){
		 steps{
		    checkout scm
		 }
         }
         stage ('Build Gradle'){
		 steps{
                   sh "gradle build"
		 }
           }
   	} 
       catch (ex) {
		echo "Some failed"
	}
         stage ('post'){
		 steps{
                    if ( currentBuild.result == 'SUCCESS') {
                        addBadge(icon: 'completed.gif', text: 'Build Success')
                       }
                    if (currentBuild.result == 'FAILURE') {
                       addBadge(icon: 'error.gif',text: 'Build Faiure')
                       }
		 }
         }
   }
}
