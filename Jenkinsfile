pipeline {
    agent any
    options {
        timeout(10)     //Restrict the job to 10mins
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '3', numToKeepStr: '3') //Discard old builds
    }
    stages {
        stage("Build") {
            steps {
                sh "echo hello"
            }    
        }
       
    }     
   
}
