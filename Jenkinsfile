def imagename = "mujeeb98/html1"
def dockerImage = ''

node {
    stage('Cloning Git') {
        git(url: 'https://github.com/Mujeeb78/HTML_1.git', branch: 'main')
    }
  
    stage('Building image') {
        script {
          dockerImage = docker.build imagename
      }
    }
    stage('Deploy Image') {
          withCredentials([usernamePassword(credentialsId: 'DocCred', passwordVariable: 'DocCredPassword', usernameVariable: 'DocCredUser')]) {
            sh "docker login -u ${env.DocCredUser} -p ${env.DocCredPassword}"
            sh 'docker push mujeeb98/html1:latest'
         
      }
        stage('Pull docker Image') {
           sh "docker pull mujeeb98/html1:latest"
              sh "docker run -d -t -p 3000:3000 --name html1container${BUILD_NUMBER}. mujeeb98/html1:latest"
            sh "docker ps"
        }
    }  
}
