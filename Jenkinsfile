node {
  def app
  stage('Clone repository') {
    checkout scm
  }
  
  stage('Build image') {
    app = docker.build("ananddocker01/nodejs-docker-pipeline")
  }
  
  stage('Test image') {
    app.inside {
      sh "echo test passed"
    }
  }
  
  stage('Push image') {
    docker.withRegistry('https://registry.hub.docker.com', 'anand_dockerid')  {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
