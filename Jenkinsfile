node {
    def npmHome = tool name: 'NodeJS', type: 'npm'
    env.PATH = "${npmHome}/bin:${env.PATH}"
    
    stage('Build') {
        steps {
            script {
                docker.image('node:16-buster-slim').withRun('-p 3000:3000') { c ->
                    sh 'npm install'
                }
            }
        }
    }
    
    stage('Test') {
        steps {
            script {
                docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                    sh './jenkins/scripts/test.sh'
                }
            }
        }
    }
}