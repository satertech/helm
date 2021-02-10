podTemplate(label: label, cloud: 'kubernetes', containers: [
    containerTemplate(name: 'helm', image: 'dtzar/helm-kubectl:3.4.0', ttyEnabled: true, command: 'cat')
  ]) {

      node{

          stage('deploy'){

              container('helm'){

                  sh 'helm install example-app example-app/'

              }
          }
      }


  }


