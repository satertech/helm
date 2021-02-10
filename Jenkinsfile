podTemplate(yaml: """\
    apiVersion: v1
    kind: Pod
    metadata:
      labels: 
        some-label: some-label-value
    spec:
      containers:
      - name: helm
        image: dtzar/helm-kubectl:3.4.0
        command:
        - cat
        tty: true
    """.stripIndent()) {
        node(POD_LABEL) {

            stage ('deploy') {
                
                container('helm') {

                    sh 'git clone https://github.com/satertech/helm.git'
                    
                    sh 'helm install example-app example-app/'

            }
        }
    }
 
}
