node {
  def remote = [:]
  remote.name = 'vm_ansible'
  remote.host = 'vm_ansible'
  remote.user = 'root'
  remote.password = 'P@ssw0rd'
  remote.allowAnyHosts = true
  stage('Remote SSH') {
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
