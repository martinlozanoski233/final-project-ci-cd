pipeline {
    agent {
       label 'agent1'
    } 
   
    environment {
       REPO_URL = 'https://github.com/martinlozanoski233/final-project-ci-cd.git' 
       TMP_DIR = '/tmp/final-project-tmp'
       NGINX_ROOT_DIR = '/home/martin/final-project-ci-cd'
       BACKUP_DIR = '/home/martin/final-project-backup' 
    }

    stages {
        stage('Clone repository') { 
            steps {
                sh '''
                rm -rf $TMP_DIR
                git clone $REPO_URL $TMP_DIR
                '''  
            }
        }
        stage('Copy to NGINX root and Backup Dir') { 
            steps {
                sh '''
                   mkdir -p $NGINX_ROOT_DIR $BACKUP_DIR
 
                   rm -rf $NGINX_ROOT_DIR/*
                   rm -rf $BACKUP_DIR/*

                   cp -r $TMP_DIR/* $NGINX_ROOT_DIR/
                   cp -r $TMP_DIR/* $BACKUP_DIR/
                '''    
            }
        }
    }
}
