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
    stage(‘Lint HTML’) {
        steps {
          sh ‘tidy -q -e *.html’
        }
    }
    stage('Upload to AWS'){
      steps {
          withAWS(region:'sa-east-1',credentials:'aws-static') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'fabiotavarespr-udacity')
          }
        }
    }
  }
}
