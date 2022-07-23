pipeline {
    agent any
    options {
        timeout(10)     //Restrict the job to 10mins
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '3', numToKeepStr: '3') //Discard old builds
    }
    environment {
        ARTIFACTORY_ACCESS_TOKEN = credentials('artifactory-access-token')
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
        stage("Artifact upload") {
            steps {
                sh """
                    /usr/local/bin/jfrog rt upload --url http://localhost:8082/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} artifacts.tar.gz code_testing/
                """
            }
        }
       
    }     
   
}
