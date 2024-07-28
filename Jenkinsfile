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
            withCredentials([usernamePassword(credentialsId: 'your-ssh-credentials-id', usernameVariable: 'SSH_USERNAME', passwordVariable: 'SSH_PASSWORD')]) {
                    sh """
                        sshpass -p "$SSH_PASSWORD" ssh $SSH_USERNAME@${params.REMOTE_HOST} '
                            mkdir -p /path/to/install
                            pwd
                            cd /path/to/install
                            wget https://raw.githubusercontent.com/mihai-pruna/Docker-Install/main/install-docker.sh                            
                            chmod +x install-docker.sh
                            ./install-docker.sh
                        '
                    """
                }
            }
        }
    }
}
