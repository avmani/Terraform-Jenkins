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
                sh "terraform apply --auto-approve"
            }
        }
    }

}

def getTerraformPath(){
    def tfHome = tool name: 'terraform-1.1.7', type: 'terraform'
    return tfHome
}