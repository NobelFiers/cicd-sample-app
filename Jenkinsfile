node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
       			                   }
    			 }

    stage('Build') {
	steps {
           git url: 'https://github.com/NobelFiers/cicd-sample-app.git', branch: 'main'
           sh 'pwd'
           script {
               if ( fileExists('tempdir') ) {
                  sh 'rm -rf tempdir/; fi'
                                  } 
       		   }
	   sh 'bash ./sample-app.sh'
           }
	}

    stage('Results') {
        build 'Test_SampleApp'
    		     }
}