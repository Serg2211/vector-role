pipeline{
    agent {
        label 'ansible'
    }
    stages{
        stage('Git'){
            steps{
                git branch: 'main', credentialsId: 'ba6e2fc3-e0bc-4fec-bb0f-7d1f8ba8ed85', url: 'git@github.com:Serg2211/vector-role.git'
            }
        }
        stage('install requirement'){
            steps{
                sh 'pip3 install --user "molecule==3.5.2" "molecule_docker" "ansible-lint<6.0.0" flake8'
                sh 'docker --version && ansible --version && ansible-lint --version && molecule --version'
                sh 'pwd'
            }
        }
        stage('Run molecule test'){
            steps{
                sh 'molecule test ubuntu_latest'
            }
        }
    }
}
