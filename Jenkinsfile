pipeline {
    agent any

    stages {
        stage('cheakout') {
            steps {
                git branch: 'main', url: 'https://github.com/tejas-tawalare/PROJECT1.git'
            }
        }
        stage('copy new  to ansible server') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'jenkinstoansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'rsync -av /var/lib/workspace/projectone/*.html root@172.31.15.66:/opt/', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
        stage('exaec playbook') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansibletoweb', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /playbook/playbook.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        }
    }
}
