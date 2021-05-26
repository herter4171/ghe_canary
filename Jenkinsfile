// Sole param is CLONE_URL
pipeline {
    agent {label 'jenkins_node_lite || master'}
    
    stages {
        
        stage('Test Clone') {
            steps {
                sh '''
                DIR_NAME=$(echo $CLONE_URL \
                    | awk -F '/' '{print $NF}' \
                    | sed 's|\\.git$||g')
                
                # Ensure no existing clone in path
                # TODO: Redundant?
                rm -rf $DIR_NAME

                # Clone dummy repo
                git clone $CLONE_URL
                '''
            }
        }
    }

    post {
        always {
            cleanWs()
        }

        failure {
            script {
                slackSend color: 'danger', message: "<@UBXJXU5NF> and <@UDVDR02JC>, connectivity issues with GHE (<${BUILD_URL}|log>)."
            }
        }

    }
}