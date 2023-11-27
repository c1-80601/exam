pipeline {
     agent any
 
     stages {
         stage ('SCM') {
             steps {
                 git branch: 'master', url: 'https://github.com/c1-80601/exam.git'
             }
         }
         stage ('docker login') {
             steps {
                 sh 'dckr_pat_ZpaCWumdUSl9RU6rVM_fapH70k4 | /usr/bin/docker login -u pratik234 --password-stdin'
             }
         }
         stage ('docker build image') {
             steps {
                 sh '/usr/bin/docker image build -t pratik234/resume .'
             }
         }
         stage ('docker push image') {
             steps {
                 sh '/usr/bin/docker image push pratik234/resume'
             }
         }
         stage ('docker remove service') {
             steps {
                 sh '/usr/bin/docker service rm myservice'
             }
         }
         stage ('docker create service') {
             steps {
                 sh '/usr/bin/docker service create --name myservice -p 9876:80 --replicas 5 pratik234/resume'
             }
         }
     }
}

