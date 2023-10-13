node {
    // Menggunakan Docker agent dengan gambar 'node:16-buster-slim'
    docker.image('node:16').withRun('-p 3000:3000') { container ->
        // Tahap Build
        stage('Build') {
            // Langkah untuk menjalankan npm install
            sh 'npm install'
        }
    }
}
