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
	stage ('Unit test'){
		steps{
		   sh "gradle test"
		}
	}
	stage ('func-test'){
		paralles{
		    steps{
			  sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar igor 'Hello Igor!'"
		    }
		    steps{
			  sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar myTest 'Hello MyTest!'"  
		    }
		    steps{
			  sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar 123 'Hello 123!'"  
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
