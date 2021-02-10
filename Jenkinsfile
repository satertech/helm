podTemplate(cloud: 'kubernetes', yaml: """
apiVersion: v1
kind: Pod
metadata:
    labels:
        jenkins/label-digest: "6ba93233d22ff0212c5c877dbc5afb06b7d3aafc"
        jenkins/jenkins-jenkins-slave: "true"
        jenkins/label: "jenkins-jenkins-slavex"
    name: "default-hdjp8"
spec:
  containers:
  - args:
    - "********"
    - "default-hdjp8"
    env:
    - name: "JENKINS_SECRET"
      value: "********"
    - name: "JENKINS_TUNNEL"
      value: "jenkins-agent:50000"
    - name: "JENKINS_AGENT_NAME"
      value: "default-hdjp8"
    - name: "JENKINS_NAME"
      value: "default-hdjp8"
    - name: "JENKINS_AGENT_WORKDIR"
      value: "/home/jenkins"
    - name: "JENKINS_URL"
      value: "http://jenkins.jenkins-project-2.svc.cluster.local:8080"
    image: "jenkins/inbound-agent:4.3-4"
    imagePullPolicy: "IfNotPresent"
    name: "jnlp"
    resources:
      limits:
        memory: "512Mi"
        cpu: "512m"
      requests:
        memory: "512Mi"
        cpu: "512m"
        tty: false
    - name: helm
    image: dtzar/helm-kubectl:3.4.0
    command: ['cat']
    tty: false
    volumeMounts:
        - mountPath: "/home/jenkins
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

