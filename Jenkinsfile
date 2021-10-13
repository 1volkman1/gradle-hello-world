#!groovy
node('slave1') {
   stage ('Checkout'){

      // Get some code from a GitHub repository
      checkout scm
      
   }
   
   stage ('Build Gradle'){

      def gradleHome = tool 'gradle4'
      // Run the maven build
      sh "${gradleHome}/bin/gradle build"
   }
}
