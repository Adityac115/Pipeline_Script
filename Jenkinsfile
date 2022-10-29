pipeline{
    agent any
    stages {
        stage('Git-checkout'){
            steps{
                echo "compiled succesfully!!";
                git credentialsId: '30fffa57-6a9c-4092-8f44-3ba0039b68bc', url: 'https://github.com/Adityac115/Pipeline_Script.git'
            }
        }
        stage('Build'){
            steps{
                echo "building the checkout project";
                bat 'Build.bat'
            }
        }
        stage('Unit'){
            steps{
            echo "JUnit Passed succesfully!!";
            bat 'Unit.bat'
            }
        }
        stage('Qaulity-Gate'){
            steps{
                echo "SonarQube Qaulity Gate Passed succesfully!!";
                /*sh exit("1");*/
                bat 'Quality.bat'
            }
        }
        stage('Deploy'){
            steps{
                echo "Pass!!";
                bat 'Deploy.bat'
            }
        }
    }
    post{
        always{
            echo 'This will always run'
        }
        success{
            echo 'This will run only if succesful'
        }
        unstable{
            echo 'This will run only if the run was marked as unastable'
        }
        changed{
            echo 'This will run only if the state of the pipeline has changed'
            echo 'For example , if the pipeline was previousily failing but is now succesful'
        }
    }
}
