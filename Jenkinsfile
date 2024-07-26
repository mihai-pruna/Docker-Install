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
                sshagent(['your-ssh-credentials-id']) {
                    sh """
                        ssh user@remote-host '
                            mkdir -p /path/to/install
                            cd /path/to/install
                            wget https://github.com/mihai-pruna/Docker-Install/blob/main/install-docker.sh
                            chmod +x install.sh
                            ./install.sh
                        '
                    """
                }
            }
        }
    }
}
