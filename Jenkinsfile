pipeline{
    agent any

    environment {
        PATH = "${PATH}:${getTerraformPath()}"
    }
    
    stages{
        stage("terraform init"){
            steps{
                sh "terraform init"
                sh "terraform version"

            }
        }

        stage("terraform fmt"){
            steps{
                sh "terraform fmt"
            }

        }

        stage("terraform apply"){
            steps{
                sh "terraform apply --auto-approve"
            }
        }

        stage("terraform destroy"){
            steps{
                sh "terraform destroy --auto-approve"
            }
        }
    }

}

def getTerraformPath(){
    def tfHome = tool name: 'terraform-1.1.7', type: 'terraform'
    return tfHome
}