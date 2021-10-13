node{
    stage('pull the code fromGithub'){
        git branch: 'main', url: 'https://github.com/chandra597712/devops-jenkins.git'
    }
    stage('building code with maven'){
        sh 'mvn clean install '
    }
    stage('buliding docker image from latestcode'){
        sh 'docker build -t chandrabydocker/cicd:v1 .'
    }
    stage('pushing '){
        withCredentials([string(credentialsId: 'Dockercreds2', variable: 'dockercreds2')]) {
        sh '''docker login -u chandrabydocker -p $dockercreds2'''
        }
        sh 'docker push chandrabydocker/cicd:v1'
        
        
    } 
}