node(Node){

    stage('git'){

        sh 'git fetch'
    }

    stage ('helm-deploy'){

        sh 'helm install example-app /kubernetes/helm/temp/example-app/'
    }
}