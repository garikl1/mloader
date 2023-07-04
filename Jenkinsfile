def imageName = 'garikl1/mloader'
node('workers'){
        stage('Checkout'){
          git branch: 'develop',
            credentialsId: 'github-ssh',
            url: 'git@github.com:garikl1/mloader.git'
        }
        stage('Unit Tests') {
          def imageTest = docker.build("${imageName}-test", "-f Dockerfile.test .")
          sh "docker run --rm -v $WORKSPACE/reports:/app/reports ${imageName}-test"
          junit "$WORKSPACE/reports/*.xml"
        }

}