node{

    stage('SCM Checkout')
    {
        git credentialsId: '7154b1ef-ece6-49cb-91d1-de2f4d959a21', url: 'https://github.com/dharish008/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u dharish008 -p ${DHPWD}"
        }
        sh 'docker push dharish008/phpmysql_app'
    }
}
