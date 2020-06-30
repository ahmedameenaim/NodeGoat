pipeline {
    agent any
    stages {
        stage('initialize') {
            steps {
                echo 'Building completed...............'
            }
        }
        
        stage('snyk dependency scan') {
 
          steps {
              echo 'dependency scan start...............'
            // sh "docker run -e SNYK_TOKEN= -e MONITOR=true -v /var/lib/jenkins/workspace/nodegoat-pipline/:/project snyk/snyk-cli:npm test  || true"
          }  
        }
        
        stage('SAST') {
            steps {
                echo 'SAST Started...............'
                sh "njsscan"
                sh "njsscan --missing-controls --json /var/lib/jenkins/workspace/nodegoat-pipline/"
             //   sh "docker pull secfigo/bandit"
             //  sh "docker run -v /var/lib/jenkins/workspace/vulnerable_python_app:/src --rm secfigo/bandit bandit -r /src || true" 
            }
        } 
       
        stage('DAST') {
            steps {
                echo 'Start Dynamic security application Testing .......'
                //sh "docker run --network='host' -t owasp/zap2docker-stable zap-baseline.py -t http://127.0.0.1:8000/ || true"
            }
        }
        stage('Security Docker Images') {
            steps {
                echo "Start Scanning Images......."
               // sh "sudo trivy mongo:3.4"
                echo "Aqua micro scanner ....."
               // sh "docker build --build-arg token=NGUwZDkyMzJiMTVm --no-cache ."
            }
        } 
    }
}
