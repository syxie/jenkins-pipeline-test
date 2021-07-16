pipeline {
 agent any
  stages {
    stage("testing"){
      steps {

            checkout scm
            sh "ls -al"
            sh "echo "
            GIT_COMMIT_HASH = gitCommitHash()
            sh "echo ${GIT_COMMIT_HASH}"
            sh "docker info"
            sh "docker images"
            // sh "docker build -t  ${image}:${branch} ."
            script {
                try {
                sh '''
                buildpush.sh -r $repository -n $repository -i $repository -c $commitHash
                '''
            } catch (Exception e) {
                sh "echo Failed to build: $e"
            }
            // sh "kubectl version"
            // sh "helm version"
        }

    }
  }
}
