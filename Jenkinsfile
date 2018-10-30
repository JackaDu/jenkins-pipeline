def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, serviceAccount: 'cd-jenkins', containers: [
    containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.12.2', ttyEnabled: true, command: 'cat'),
  ]) {
    node(label) {
        stage('testing kubectl') {
            container('kubectl') {
                sh 'kubectl apply -f https://k8s.io/examples/application/deployment.yaml'
            }
        }
    }
}
