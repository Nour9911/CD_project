pipeline {
  agent any
  stages {
    stage("Pull") {
      steps {
        script {
          checkout([$class: 'GitSCM',
            branches: [[name: '*/main' ]],
            userRemoteConfigs: [[
            url: 'https://github.com/anas1412/Myapp.git',
            credentialsId: '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'
            ]]
            ])
          }
        }
    }
  }
}
