node {
    def app
    stage ("clone repository"){
        checkout scm
    }
    stage ('Update GIT'){
        script {
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                withCredentials([usernamePassword(credentialsId: 'github',passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]){
                    sh "git config user.email mamunurr191@gmail.com"
                    sh "git config user.name mamunurrashid420"
                    sh "cat deployment.yaml"
                    sh "sed -i 's+mamunurrashid123/python.*+mamunurrashid123/python:${DOCKERTAG}+g' deployment.yaml"
                    sh "cat deployment.yaml"
                    sh "git add ."
                    git " git commit -m 'Done by jenkins job : ${env.BUILD_NUMBER}'"
                    sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
                   
                }
            }
        }
    }
}