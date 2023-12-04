node {
    def mvnHome = tool 'maven-3.9.5'
    def dockerImage
    def dockerImageTag = "devopsexample${env.BUILD_NUMBER}"
    
    stage('Clone Repo') {
      git 'https://github.com/dominique-coder/Jenkins-Test.git'
    }    
  
    stage('Build Project') {
      //sh "'${mvnHome}/bin/mvn' -B -DskipTests clean package"
    }
        
    stage('Build Docker Image') {
      //sh "docker -H tcp://192.168.8.100:237 build -t devopsexample:${env.BUILD_NUMBER} ."
	    sh "docker -H tcp://127.0.0.0:8 build -t devopsexample:${env.BUILD_NUMBER} ."
    }
    
    stage('Deploy Docker Image'){
      	echo "Docker Image Tag Name: ${dockerImageTag}"
	sh "docker -H tcp://127.0.0.0:8 run --name devopsexample -d -p 2222:2222 devopsexample:${env.BUILD_NUMBER}"
    }
}
