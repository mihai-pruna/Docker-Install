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
            withCredentials([sshUserPrivateKey(credentialsId: 'your-ssh-credentials-id', keyFileVariable: 'SSH_KEY_FILE')]) {
                    sh """
                        ssh -i $SSH_KEY_FILE user@${params.REMOTE_HOST} '
                            mkdir -p /path/to/install
                            cd /path/to/install
                            wget https://your-script-url/install.sh
                            chmod +x install.sh
                            ./install.sh
                        '
                    """
                }
            }
        }
    }
}
