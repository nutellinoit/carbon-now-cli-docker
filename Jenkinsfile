node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        checkout scm
    }

    stage('Copy dir') {
        sh "cp -r carbon-now-cli build-docker/rootfs"
    }

    stage('Build image') {
        app = docker.build("nutellinoit/carbon-now-cli-docker","--pull build-docker/")
    }

    stage('Delete dir') {
        sh "rm -rf build-docker/rootfs || true"
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
