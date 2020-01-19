pipeline {
    agent any
    stages {
        stage('initialize') {
            steps {
                echo 'Building completed...............'
            }
        }
        
    stage('snyk dependency scan') {
        
      environment {
        SNYK_TOKEN = credentials('Synk-agent')
      }	
      steps {
        sh """
          snyk auth ${SNYK_TOKEN}
          snyk test --json \
            --severity-threshold=high \
            --file=yarn.lock \
            --project-name=nodegoat
        """		
      }
    }
        
        stage('scan app packges') {
            steps {
            echo "start scan app depenicies"
          //  sh "synk test"    
            }
        }
        
        stage('SAST') {
            steps {
                echo 'SAST completed...............'
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
