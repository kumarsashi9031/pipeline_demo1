@Library('jenkins-shared-library@master') import static org.foo.Utilities.*
import static org.foo.Gitcheckout.*
node {
  stage('Git-Checkout') { 
        echo "checking out from git repo";
                git this,'https://github.com/javaparser/javaparser-maven-sample.git'
                
        }
        stage('Build') { 
                
                notifystarted()
                 mvn this, 'clean install'
                notifySuccessful()
                
                
        }
        
        // stage('deployment of an agent'){
        //         sshagent(['4a2572d4-8cde-4d54-b399-e767fd7c4413']) {
        //            sh "scp target/**.jar ubuntu@ec2-52-90-87-94.compute-1.amazonaws.com:/home/ubuntu/slave3"
        //         }    
        // }
        
    
    stage('archive the artifact') {
            archiveArtifacts artifacts: 'target/**.jar'
             } 
        
}
