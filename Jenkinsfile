#!groovy
pipeline{
    agent {
    label 'slave1'
    }
       tools {
           gradle 'gradle4'
        }
   stages {
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
        post{
		 success {
                        addBadge(icon: 'completed.gif', text: 'Build Success')
                       }
                 failure {
                       addBadge(icon: 'error.gif',text: 'Build Faiure')
                       }
            }
         }
}
