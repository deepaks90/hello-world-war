pipeline{
      agent { label 'master' }
      stages{
      stage('check out'){
                  steps{
                  sh "rm -rf hello-world-war"
                  sh "git clone https://github.com/deepaks90/hello-world-war.git"
                  }
                  }
      stage('build'){
      steps{
      sh "pwd"
      sh "ls"
      sh "cd hello-world-war"
      sh "docker build -t deepaks90/docwarimage:1.0 ."
      }
      }
       stage('publish'){
                  steps{
                        sh "docker login -u deepaks90 -p Deep@k123"
                        sh "docker push  deepaks90/docwarimage:1.0"
                  }
            }
            stage('deploy'){
                  agent { label 'slave1' }
                  steps{
                        sh "docker login -u deepaks90 -p Deep@k123"
                        sh "docker pull deepaks90/docwarimage:1.0"
                        sh "docker rm -f trail1"
                        sh "docker run -d -p 8086:8080 --name trail1 deepaks90/docwarimage:1.0"
                  }
            }
      }
      }
