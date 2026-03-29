DOCKER JAVA PROJECT


pipeline {
 agent any
 tools {
 maven "mymaven"
 }
 stages {
 stage('CleanWs') {
 steps {
 cleanWs()
 }
 }
 stage ("Code") {
 steps {
 git "https://github.com/LokeshPonthala/FacebookApp.git"
 }
 }
 stage ("Build") {
 steps {
 sh 'mvn clean package'
 sh 'cp -r target Docker-app'
 }
 }
 stage ("CQA") {
 steps {
 withSonarQubeEnv('mysonar') {
 sh "mvn clean verify sonar:sonar -Dsonar.projectKey=MyProject"
 }
 }
 }
 stage ("Quality Gates") {
 steps {
 script {
 waitForQualityGate abortPipeline: false, credentialsId: 'sonar-token'
 }
 }
 }
 stage ("Artifact") {
 steps {
 nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file:
'target/vprofile-v2.war', type: 'war']], credentialsId: 'nexus', groupId: 'com.visualpathit',
nexusUrl: '3.86.149.224:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'myrepo',
version: 'v2'
 }
 }
 stage ("Images") {
 steps {
 sh 'docker build -t appimage Docker-app'
 sh 'docker build -t dbimage Docker-db'
 }
 }
 stage ("ImageScan") {
 steps {
 sh 'trivy image appimage >> appimage-report.txt'
 sh 'trivy image dbimage >> dbimage-report.txt'
 }
 }
 stage ("deploy") {
 steps {
 sh 'docker-compose up -d'
 }
 }
 }
}


###### I have deployed to eks cluster also by creating with terraform and successfully accessed the Application #######

stage ("Configure EKS") {
   steps {
    sh '''
    aws eks --region us-east-1 update-kubeconfig --name eks-cluster-cloud
    '''
   }
  }

  NEW: Deploy to EKS
  stage ("Deploy to EKS") {
   steps {
    sh '''
    kubectl apply -f k8s/deployment.yaml
    kubectl apply -f k8s/service.yaml
    '''
   }
  }


  
