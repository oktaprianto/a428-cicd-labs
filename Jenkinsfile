node {
    def dockerImage = 'node:16-buster-slim'
    
    stage('Build') {
        steps {
            script {
                def buildResult = docker.image(dockerImage).inside("-p 3000:3000") {
                    sh 'npm install'
                }
                if (buildResult != 0) {
                    error "Build failed"
                }
            }
        }
    }
    
    stage('Test') {
        steps {
            script {
                def testResult = docker.image(dockerImage).inside("-p 3000:3000") {
                    sh './jenkins/scripts/test.sh'
                }
                if (testResult != 0) {
                    error "Tests failed"
                }
            }
        }
    }
    
    
}
