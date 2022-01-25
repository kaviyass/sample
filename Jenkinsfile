pipeline {
  agent any
  stages  {
    stage('Deploy to Kubernetes'){
      steps{
       script {
         bat 'cd .kube && kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" get nodes'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" get pods --namespace=workflow-tools'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" create secret generic mysql --from-literal=password=root'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" get secret mysql -o yaml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f pv.yml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f pvc.yml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f mysql.yaml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f mysql-service.yaml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f mautic.yml'
         bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" apply -f mautic-service.yml'
         //bat 'kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" port-forward pod/mautic-5bf58558c6-z6ml4 80:80'
      // bat 'kubectl --kubectl --kubeconfig="tf-k8s-01f25f2617-kubeconfig.yaml" get svc mautic-service -o yaml
         
        }
      }
    }
  }
} 
