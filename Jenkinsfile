pipeline {
  agent any
    stages {
        stage("Tests") {
            steps {
              script{
                try {
                  sh "docker run --rm -v /var/jenkins_home/workspace/TestTaurus2:/bzt-configs -v /var/jenkins_home/workspace/TestTaurus2/reports:/tmp/artifacts blazemeter/taurus example.yml"
                } finally {
                  junit 'reports/report.xml'
                  perfReport filterRegex: '', showTrendGraphs: true, sourceDataFiles: 'reports/xml-jenkins.xml'
                  cleanWs()
                }
              }
            }
        }
    }
}