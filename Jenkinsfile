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
           steps {
            sshCommand remote: remote, command: "yum update --nobest -y"
            sshCommand remote: remote, command: "yum install python3 -y"
            sshCommand remote: remote, command: "yum install git -y"
            sshCommand remote: remote, command: "dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo"
            sshCommand remote: remote, command: "dnf install --nobest docker-ce -y"
            sshCommand remote: remote, command: "git init"
            sshCommand remote: remote, command: "git pull https://github.com/irakholla/project.git"
            sshCommand remote: remote, command: "chmod '+x' jen/pipeline.sh"
            sshCommand remote: remote, command: "jen/pipeline.sh"
            sshCommand remote: remote, command: "cat jen/my_password.txt | docker login --username irakholla --password-stdin"
            sshCommand remote: remote, command: "docker build -t irakholla/jen_web:web "
            sshCommand remote: remote, command: "docker push irakholla/jen_web:web"
           }
        }
    }
}

