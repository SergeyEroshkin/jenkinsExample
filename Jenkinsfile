pipeline {
  agent any
  stages {
    stage('HELLO') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withMaven(jdk: 'JDK 8u172', maven: 'Maven 3.6.3') {
                        sh 'mvn clean install'
                    }
                }
            }
          steps {
              allure([includeProperties: true,
                                    jdk: '',
                             properties: [],
                      reportBuildPolicy: 'ALWAYS',
                                results: [[path: '**/allure-results']]
              ])
          }
    }
    }
}