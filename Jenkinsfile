node{

   def tomcatWeb = 'C:\\Program Files\\apache-tomcat-9.0.58\\webapps'
   def tomcatBin = 'C:\\Program Files\\apache-tomcat-9.0.58\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/janmeshmathur/maven/blob/1b39935cf99c6e3f445bdaebd5ea168f3d240238/Jenkinsfile'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
