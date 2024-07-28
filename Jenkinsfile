pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mihai-pruna/Docker-Install.git'
            }
        }

        stage('Remote Connection') {
            steps {
            #sh "sudo apt-get update && sudo apt-get install -y sshpass"
            
            withCredentials([usernamePassword(credentialsId: 'your-ssh-credentials-id', usernameVariable: 'SSH_USERNAME', passwordVariable: 'SSH_PASSWORD')]) {
                    sh """
                        ssh -p "$SSH_PASSWORD" ssh $SSH_USERNAME@${params.REMOTE_HOST} '
                            mkdir -p /path/to/install
                            cd /path/to/install
                            wget https://github.com/mihai-pruna/Docker-Install/blob/main/install-docker.sh
                            chmod +x install-docker.sh
                            ./install-docker.sh
                        '
                    """
                }
            }
        }
    }
}
