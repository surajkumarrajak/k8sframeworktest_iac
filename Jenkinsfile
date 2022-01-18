node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                                           //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "cat deployment.yaml"
                        sh "sed -i 's+myapp.*+myapp:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push origin master"
      }
    }
  }
}

