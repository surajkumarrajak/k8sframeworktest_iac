
node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email suraj@gmail.com"
                        sh "git config user.name Suraj"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+myapp.*+myapp:${params.DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
			//sh "git push git@github.com:surajkumarrajak/k8sframeworktest_iac.git HEAD:master" 
			sh "git push https://surajkumarrajak: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@github.com/surajkumarrajak/k8sframeworktest_iac.git HEAD:master"

     }
    }
  }
}

