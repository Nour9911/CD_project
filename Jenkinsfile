pipeline {
  agent any
  stages {
    stage("Pull") {
      steps {
        script {
          checkout([$class: 'GitSCM',
            branches: [[name: '*/main' ]],
            userRemoteConfigs: [[
            url: 'https://github.com/Nour9911/MyApp.git',
            credentialsId: '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'
            ]]
            ])
          }
        }
    }
  }
}
