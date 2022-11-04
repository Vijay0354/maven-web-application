node {

def mavenHome = tool name: "maven3.8.5"

echo "Build number: ${env.BUILD_NUMBER}"
//echo "Job name is : ${env.JOB_name}"
echo "Node name is : ${env.NODE_NaME}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '6')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

stage('CheckoutCode'){
git branch: 'development', credentialsId: '8dd2f226-6643-4b6c-99bb-6964a4b6b427', url: 'https://github.com/Vijay0354/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarQubeReport'){
sh "mvn sonar:sonar"
}

stage ('UploadArtifactintoNexus')
{
sh "mvn deploy"
}

stage('DeployAppintoTomcatServer'){
sshagent(['51e4967a-34c5-456b-8e74-aad1064e206f']) {
    sh "scp -o StrictHostKeyChecking=no
target/maven-web-application.war ec2-user@172.31.7.84:/opt/apache-tomcat-9.0.68/webapps/"

}
}

*/
}
