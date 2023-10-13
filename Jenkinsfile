node {
    checkout scm

    docker.image('node:16-buster-slim').withRun('-p 3000:3000') {
        def npmPath = tool name: 'NodeJS', type: 'Tool'
        def npmHome = tool name: 'NodeJS', type: 'Tool' // Or you can specify a custom node tool home directory here

        withEnv(["PATH+${npmHome}/bin", "PATH+${npmPath}/bin"]) {
            stage('Build') {
                sh 'npm install'
            }

            stage('Test') {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
