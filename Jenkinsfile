pipeline{
    agent any

    environment{
        NODE_VERIONS = '18.x'
    }

    tools{
        nodejs "${NODE_VERIONS}"
    }

    stages{
        stage("Checkout"){
            steps{
                checkout scm
            }
        }

        stage("Install dependencies"){
            steps{
                script{
                    if(isUnix()){
                        sh 'npm install'
                    }
                    else{
                        sh 'npm install'
                    }
                }
            }
        }

        stage("Start application and run tests"){
            steps{
                script{
                    sh 'npm start &'
                    sh 'wait-on http://localhost:8090'
                    sh 'npm test'
                }
            }
        }
    }

    post{
        always{
            echo "CI pipeline completed"
        }
    }
}