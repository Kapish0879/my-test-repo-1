pipeline 
{

    agent {
        label 'kapish'
    }

    tools {
       // npm 'npm-app-18'
       nodejs 'npm-web-16'
        //dockerTool 'my-docker'
    }
  
    stages {

        stage('Git Checkout') {
            steps {

                git url: 'https://github.com/Kapish0879/my-test-repo-1.git'

                echo "Code Checked-out Successfully!!"

                sh 'ls -la'
            }
        }

        
        stage('Create Artifact') {

            steps {
                sh '''
                npm run build
                '''
            }
        }

        /*stage('sonarQube Analysis') {
            steps {

                withSonarQubeEnv('sonar') {
                    sh 'mvn clean verify sonar:sonar'
                }

                echo "SonarQube Analysis Completed Successfully!!"
            }
        }

        stage('Package') {
            steps {

                sh 'npm run build'

                echo "NPM Package Goal Executed Successfully!"
            }
        }

        stage('Docker Build') {
            steps {

                sh 'docker --version'

                sh 'docker images'

                sh 'docker build -t $calcwebappmvn:$BUILD_NUMBER .'

                echo "Docker Image Built Successfully!!"

                sh 'docker images'
            }
        }
        //pushing image to aws ecr
        stage('Docker Push') {
            steps {

                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 964742912902.dkr.ecr.us-east-1.amazonaws.com'

                sh 'docker tag $calcwebappmvn:$BUILD_NUMBER 964742912902.dkr.ecr.us-east-1.amazonaws.com/dev/project:$BUILD_NUMBER'

                sh 'docker push 964742912902.dkr.ecr.us-east-1.amazonaws.com/dev/project:$BUILD_NUMBER'

                echo "Docker Image Pushed to AWS ECR Successfully!!"
            }
        }
        // replace image name 
         stage('Replace Image') {
            steps {
                sh """
                sed -i "s|PLACEHOLDER_IMAGE|${IMAGE_NAME}|g" deployment.yaml
                """
            }
        }
        //deploying image to aws eks
        stage('Deploy to EKS') {
            steps {
                sh 'kubectl version --client'

                sh 'kubectl config set-context --current --namespace=jenkins'

                sh 'kubectl get nodes'

                sh 'aws eks update-kubeconfig --region us-east-1 --name my-cluster'

                sh 'kubectl apply -f deployment.yaml'

                sh 'kubectl get pods'

                echo "Application Deployed to AWS EKS Successfully!!"
            }
        }*/
        
    }

    post {

        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
