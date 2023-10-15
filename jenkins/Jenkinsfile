node {
    def dockerImage = 'node:16-buster-slim'

    stage('Build') {
        try {
            checkout scm
            docker.image(dockerImage).inside("-p 3000:3000") {
                sh 'npm install'
                // Additional build steps can be added here if needed
            }
        } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            throw e
        }
    }
}
