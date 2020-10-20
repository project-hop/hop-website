pipeline {
    agent any

    options {
        buildDiscarder(
            logRotator(artifactNumToKeepStr: '5', numToKeepStr: '10')
        )

        timestamps()

        checkoutToSubdirectory('hop-website')
    }

    environment {
        ANTORA_CACHE_DIR  = "$WORKSPACE/.antora-cache"
        YARN_CACHE_FOLDER = "$WORKSPACE/.yarn-cache"
    }

    stages {
        stage('Theme') {
            agent {
                dockerfile {
                    dir 'hop-website'
                    label "hop-website"
                    reuseNode true
                }
            }

            environment {
                HOME = "$WORKSPACE"
            }

            steps {
                sh "cd $WORKSPACE/hop-website/antora-ui-hop && yarn --non-interactive --frozen-lockfile install"
                sh "cd $WORKSPACE/hop-website/antora-ui-hop && yarn --non-interactive --frozen-lockfile build"
            }
        }

        stage('Website') {
            agent {
                dockerfile {
                    dir 'hop-website'
                    label "hop-website"
                    reuseNode true
                }
            }

            environment {
                HOME = "$WORKSPACE"
            }

            steps {
                sh "cd $WORKSPACE/hop-website && yarn --non-interactive --frozen-lockfile install"
                sh "cd $WORKSPACE/hop-website && yarn --non-interactive --frozen-lockfile build"
            }
        }

        /*
        stage('Checks') {
            agent {
                dockerfile {
                    dir 'hop-website'
                    label "hop-website"
                    reuseNode true
                }
            }

            environment {
                HOME = "$WORKSPACE"
            }

            steps {
                sh "cd $WORKSPACE/hop-website && yarn --non-interactive --frozen-lockfile checks"
            }
        }
        */
        stage('Preview') {
            when {
                not {
                    branch 'master'
                }
            }

            steps {
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'hop-website/public', reportFiles: 'index.html', reportName: 'Preview', reportTitles: ''])
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            
            steps {
                sh '''
                cp -a ./hop-website/public/* /var/www/project-hop.org/html/
                '''
            }
       }
    }
    post { 
        always { 
            cleanWs()
        }
    }
}
