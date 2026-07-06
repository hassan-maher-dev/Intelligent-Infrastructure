pipeline {

    agent any
 
  
    stages {
 
        stage('Checkout Code') {

            steps {

                echo " Checking out repository..."

                git branch: 'main', url: 'https://github.com/hassan-maher-dev/HelloApp.git'

            }

        }
 
        stage('Terraform Init') {

            steps {

                echo " Initializing Terraform..."

                sh 'terraform init -reconfigure'

            }

        }
 
        stage('Terraform Plan') {

            steps {

                echo " Creating Terraform plan..."

                sh 'terraform plan -out=tfplan'

            }

        }



       stage('Terraform Apply') {

            steps {

                echo " Applying Terraform..."

                sh 'terraform apply -auto-approve tfplan'

                echo " Infrastructure deployed successfully!"

            }

        }



/*       stage('Terraform Destroy') {

            steps {

                echo " Destroying Terraform infrastructure..."

                sh 'terraform destroy -auto-approve'

                echo " Infrastructure destroyed successfully!"

            }

        }
*/

 }
 
    post {

        always {
            // هذا الأمر سيعمل دائماً في النهاية لتنظيف المساحة 
            echo " Cleaning up workspace to save disk space..."
            deleteDir() 
        }

        success {

            echo " Pipeline completed successfully!"

        }

        failure {

            echo " Pipeline failed!"

        }

    }
}
