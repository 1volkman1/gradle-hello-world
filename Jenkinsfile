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
            sh "gradle clean build"
		 }
      }
	  stage ('Unit test'){
		 steps{
		   sh "gradle test"
		}
	  }
	  stage ('func-test'){
		parallel{
		    stage('one'){
		      steps{
			    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar igor 'Hello Igor!'"
		      }
		    }
		    stage('two'){
		      steps{
			    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar Playtika 'Hello Playtika!'"  
		      }
		    }
		    stage('three'){
		      steps{
			    sh "sh test-data/int-test.sh build/libs/oto-gradle-1.0.jar 123 'Hello 123!'"  
		      }
		    }
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
         always {
            junit "build/test-results/junit-platform/*.xml"
            deleteDir()
         }
            }
}
