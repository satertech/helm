// podTemplate(cloud: 'kubernetes', yaml: """
// apiVersion: v1
// kind: Pod
// metadata:
//     labels:
//         jenkins/label-digest: "6ba93233d22ff0212c5c877dbc5afb06b7d3aafc"
        jenkins/jenkins-jenkins-slave: "true"
        jenkins/label: "jenkins-jenkins-slavex"
    name: "default-hdjp8"
spec:
  containers:
    - name: "helm"
    image: dtzar/helm-kubectl:3.4.0
    command: ['cat']
    tty: false
    volumeMounts:
        - mountPath: "/home/jenkins"
          name: "workspace-volume"
          readOnly: false
    workingDir: "/home/jenkins"
nodeSelector:
    kubernetes.io/os: "linux"
restartPolicy: "Never"
serviceAccount: "default"
volumes:
- emptyDir:
  medium: ""
  name: "workspace-volume"

""")

{
    node{

        stage ('deploy') {

            container('helm') {

                sh 'helm install example-app example-app/'

            }
        }
    }
}

