podTemplate(yaml: """\
    apiVersion: v1
    kind: Pod
    metadata:
      labels: 
        some-label: example-app
    spec:
      containers:
      - name: helm
        image: dtzar/helm-kubectl:3.3.0
        command:
        - cat
        tty: true
    """.stripIndent()) {
        node(POD_LABEL) {
            
            stage('loadFiles') {
                
               checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/satertech/helm']]])
            }
            

            stage ('deploy') {
                
                container('helm') {
                    
                    sh label: '', script: 'helm upgrade --install --namespace=default example-app example-app/'

            }
        }
    }
 
}
