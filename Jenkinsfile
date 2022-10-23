node {
    
    def maven_home = tool name: "MAVEN_HOME"
    stage ('clone') {
        git branch: 'develop', changelog: false, credentialsId: '4f9f1da6-dbda-4ea9-94a2-5c138f9b850a', poll: false, url: 'https://github.com/narayana3619/tech_mahindra.git'
    }
    stage ('clean') {
        sh "${maven_home}/bin/mvn clean"
    }
    stage ('compile') {
        sh "${maven_home}/bin/mvn compile"
    }
    
    stage ('test') {
        sh "${maven_home}/bin/mvn test"
    }
    
    stage ('package') {
        sh "${maven_home}/bin/mvn package"
    }
    
    stage ('verify') {
        sh "${maven_home}/bin/mvn verify"
    }
    
    stage ('install') {
        sh "${maven_home}/bin/mvn install"
    }
    '''stage ('tomcat') {
        sshagent(['1043b23a-5d21-4c3e-aa06-64abd5d46246']) {
            sh "scp -v -o StrictHostKeyChecking=no target/*.war ec2-user@18.236.183.148:/opt/18.236.183.148/webapps/"
            
        }
    }'''
    stage ('mail') {
        emailext body: 'build over scripted way', subject: 'build-over scripted way', to: 'swamy.visit@gmail.com'
    }
}
