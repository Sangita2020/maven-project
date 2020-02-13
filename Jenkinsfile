pipeline {

agent any

stages
{

stage('cloning code')

{

steps

{git 'https://github.com/Sangita2020/maven-project.git'
}
}

stage('compile my project')
{
steps
{
withMaven(jdk: 'javaJDK', maven: 'localMaven') {
    sh 'mvn compile'
}}}
    
stage('test my project')
{
steps
{
withMaven(jdk: 'javaJDK', maven: 'localMaven') {
    sh 'mvn test'
}}}
    
stage('package my project')
{
steps
{
withMaven(jdk: 'javaJDK', maven: 'localMaven') {
    sh 'mvn package'
}}}
    

    
        
stage('package my install')
{
steps
{
withMaven(jdk: 'javaJDK', maven: 'localMaven') {
    sh 'mvn install'
}}}
	
   
	
	
stage('deploy to  tomcat')
{
steps
{
    sshagent(['tomcat']) {
	 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.45.53:/var/lib/tomcat/webapps'
						}
}
}
    
    
    

}
}
