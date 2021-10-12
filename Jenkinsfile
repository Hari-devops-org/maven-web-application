node('wallmart-node')
{
    def mavenHome = tool name: "maven3.6.2"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])     

    stage('CheckOutCode'){ 
    git branch: 'development', credentialsId: '62c69cd5-3edb-474d-a53d-37ecc46efc3d', url: 'https://github.com/Hari-devops-org/maven-web-application.git'
    }
    
    stage('Build'){
    if(isUnix()){
    sh "${mavenHome}/bin/mvn clean package" 
    }
    else{

    bat "${mavenHome}/bin/mvn clean package" 
    }
    }
    /*
    stage('ExecuteSonarQubeReport'){
    sh "${mavenHome}/bin/mvn clean sonar:sonar"
    }
    stage('Upload artifact into Nexus Repo'){
    sh "${mavenHome}/bin/mvn clean deploy"
    }
    stage('DeployTheApplicationIntoTomcat'){
    sshagent(['a07429b0-6f6f-45fd-baa0-1a230920c05f']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.231.95:/opt/apache-tomcat-9.0.53/webapps"
    }
    }
    
    stage ('SendEmailNotification'){
    mail bcc: 'haridasuk15@gmail.com', body: '''Build over!!

    Regards
    Haridas''', cc: 'haridasuk15@gmail.com', from: '', replyTo: '', subject: 'Build over!!', to: 'haridasuk15@gmail.com'
    }
    */
}//closing bracket for node
