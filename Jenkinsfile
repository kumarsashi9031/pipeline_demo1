pipeline {
    agent any
 libraries {
  lib('jenkins-shared-library@master')
}
   
    stages {
        stage('Git-Checkout') { 
            steps {
            // def z = new org.foo.gitcheckout()
            //   z.checkOutFrom(repo)
                echo "checking out from git repo";
                git 'https://github.com/javaparser/javaparser-maven-sample.git'
                
                // 
            }
        }
        stage('Build') { 
            steps {
                notifystarted()
                sh 'mvn clean install'
                // notifySuccessful()
                
                
          }
        }
        
        // stage('deployment of an agent'){
        //     steps {
        //         sshagent(['4a2572d4-8cde-4d54-b399-e767fd7c4413']) {
        //            sh "scp target/**.jar ubuntu@ec2-52-90-87-94.compute-1.amazonaws.com:/home/ubuntu/slave3"
        //         }   
        //     }   
        // }
        
    } 
    post('archive the artifact') {
        success {
            archiveArtifacts artifacts: 'target/**.jar'
            
        } 
    }
        
}