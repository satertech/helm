podTemplate(cloud: 'kubernetes', yaml: """
apiVersion: v1
kind: Pod
metadata:
    labels:
        jenkins/kube-default:true
        app: jenkins
        component: agent
spec:
    containers:
    - name: helm
    image: dtzar/helm-kubectl:3.4.0
    command: ['cat']
    tty:true
    volumeMounts:
        -name: dockersock
         mountPath: /var/run/docker.sock
volumes:
    - name: dockersock
      mountPath: /var/run/docker.sock
nodeSelector:
    beta.kubernetes.io/os: linux
tolarations:
    -key: cattle.io/os
     operations: Equal
     valu: linux
     effect: NoSchedule

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

