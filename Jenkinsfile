pipeline {
    agent any
    options {
        timeout(10)     //Restrict the job to 10mins
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '3', numToKeepStr: '3') //Discard old builds
    }
    stages {
        stage("Creating tarball") {
            steps {
                sh """
                    cd  /var/lib/jenkins/workspace/CI
                    rm -f *tar.gz
                    tar -cvf artifacts.tar.gz --exclude=Jenkinsfile *
                """
            }    
        }
       
    }     
   
}
