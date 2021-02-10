callContainer([name:"helm",image:"dtzar/helm-kubectl:3.4.0"]){

    node{

        stage ('deploy') {

            container('helm'){

                sh 'helm install example-app example-app/'


            }
        }
    }
}

