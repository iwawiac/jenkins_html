def remote=[:]
remote.name = 'admin'
remote.host = '192.168.0.195'
remote.allowAnyHosts = true

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                script{
                    remote.user='admin'
                    remote.password='admin'
                }
                sshCommand(remote: remote, command: "rm -rf ~/jenkins_html")
                sshCommand(remote: remote, command: "rm -rf /opt/tomcat/webapps/jenkins_html")

                sshCommand(remote: remote, command: "git clone https://github.com/iwawiac/jenkins_html.git")
                sshCommand(remote: remote, command: "cp -r ~/jenkins_html /opt/tomcat/webapps/")

            }
        }
    }
    post {
        always {
            sleep 5
        }
    }
}
