
pipeline 
{
  agent any

  
  stages {
      
       stage ('clone')
    {
        steps{
        git 'https://github.com/onkardevops7m/webapp.git'
             }
    }

       stage ('build')
    {
        steps{
            sh label: '', script: 'mvn clean package'
             }
    }
    
       stage ('deploy')
    {
        steps{
        sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''cd /root/.ansible/roles/
ansible-galaxy install zaxos.tomcat-ansible-role
rm -rf Project2-CICD-Ansible
git clone https://github.com/onkardevops7m/Project2-CICD-Ansible.git
ansible-playbook Project2-CICD-Ansible/tomcat_install.yml
ansible-playbook Project2-CICD-Ansible/app_deploy.yml''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//root/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'target/mvn-hello-world.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
             }
    }
     
   
          }
     
}
