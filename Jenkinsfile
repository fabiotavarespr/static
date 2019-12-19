pipeline{
  agent any
  stages {
    stage('Build'){
      steps {
        sh 'echo "Hello Wolrd"'
        sh  '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
      }
    }
    stage('Upload to AWS'){
      steps {
          withAWS(region:'sa-east-1',credentials:'jenkins') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'fabiotavarespr-udacity')
          }
        }
    }
  }
}
