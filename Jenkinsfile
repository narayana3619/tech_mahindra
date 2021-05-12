node ('master) {
      def mavenHome = tool name: "MAVEN3.8.1"
      
      stage ('clone')
      {
        git branch: 'test', changelog: false, credentialsId: 'c40b1dda-5106-4492-83cb-ba6d0e2309c3', poll: false, url: 'https://github.com/narayana3619/tech_mahindra.git'
        
      }
      stage ('clean'){
        sh "mvn clean"
      }
      
      stage ('build'){
        sh "mvn package"
      }
      
      stage ('quality'){
        sh "mvn sonar:sonar"
      }
      
      stage ('deploy'){
        sh "mvn deploy"
      }
      
      stage('tomcat'){
      
        
      }
      
      stage ('mail'){
        emailext body: '''subject : build done
        Regards,
        Narayana''', 
          subject: 'build-over', 
          to: 'narayana.vist@gmail.com'
      }
      
  
