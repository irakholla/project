def remote = [:]
                remote.name = '192.168.1.107'
                remote.host = '192.168.1.107'
                remote.user = 'root'
                remote.password = 'P@ssw0rd'
                remote.allowAnyHosts = true
pipeline {
    agent any
    stages {
        stage('remote') {
            sshCommand remote: remote, command: "mkdir project_web"
            sshCommand remote: remote, command: "cd project_web"
            sshCommand remote: remote, command: "yum update -y"
            sshCommand remote: remote, command: "yum install python3 -y"
            sshCommand remote: remote, command: "yum install git -y"
            sshCommand remote: remote, command: "git init"
            sshCommand remote: remote, command: "git pull https://github.com/irakholla/project.git"
            sshCommand remote: remote, command: "chmod '+x' jen/pipeline.sh"
            sshCommand remote: remote, command: "jen/pipeline.sh"
        }
    }
}

