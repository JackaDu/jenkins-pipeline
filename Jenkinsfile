def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, serviceAccount: 'cd5-jenkins', containers: [
    containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.12.2', ttyEnabled: true, command: 'cat'),
  ]) {
    node(label) {
        stage('testing kubectl') {
            git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('kubectl') {
                stage('try kubectl') {
                    sh 'kubectl get pods'
                }
            }
        }
    }
}
