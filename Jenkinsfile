pipeline{
    agent any

    stages{
        stage('Git check'){
            steps{
                git branch: 'main', url: 'https://github.com/numan05/sample_CICD.git'
            }

        }
        stage("test PythonEnv") {
            withPythonEnv('python3') {
                sh 'pip install pytest'
                sh 'pytest mytest.py'
            }
        }
        }
    }
}