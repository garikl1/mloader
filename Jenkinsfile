def imageName = 'garikl1/mloader'
node('workers'){
        stage('Checkout'){
          git branch: 'develop',
            credentialsId: 'github-ssh',
            url: 'git@github.com:garikl1/mloader.git'
        }
        stage('Unit Tests') {
          sh "docker build -t ${imageName}-test -f Dockerfile.test ."
          sh "docker run --rm ${imageName}-test"
        }

}