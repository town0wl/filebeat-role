pipeline {
    agent {
        label 'ansible'
    }

    stages {
        stage('Download') {
            steps {
                dir('filebeat-role') {
                    git branch: 'main', url: 'https://github.com/town0wl/filebeat-role.git'
                }
            }
        }
        stage('Prepare') {
            steps {
                dir('filebeat-role') {
                    sh '[ ! -d "molecule/tox/files" ] && mkdir molecule/tox/files || true'
                    sh 'pip3 install -r test-requirements.txt'
                }
            }
        }
        stage('Run molecule') {
            steps {
                dir('filebeat-role') {
                    sh 'molecule test -s tox'
                }
            }
        }
    }
}
