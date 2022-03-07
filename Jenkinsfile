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

        stage("Create S3 Bucket"){
            steps{
                script{
                    CreateS3Bucket('my-tf-test-bucket-mani-av')
                }
            }
        }
    }

}

def getTerraformPath(){
    def tfHome = tool name: 'terraform-1.1.7', type: 'terraform'
    return tfHome
}

def CreateS3Bucket(bukcnetname){
    sh returnStatus: true, script: "aws s3 mb ${bucketName} --region=ap-south-1"

}