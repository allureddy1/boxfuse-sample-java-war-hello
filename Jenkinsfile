pipeline {
    agent any

    tools {
        maven 'maven3.9' // Ensure this matches "Global Tool Configuration"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/allureddy1/boxfuse-sample-java-war-hello.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sh '''
                    export ANSIBLE_HOST_KEY_CHECKING=False
                    ansible-playbook -i /etc/ansible/hosts ansible-playbook.yaml
                '''
            }
        }
    }
}
