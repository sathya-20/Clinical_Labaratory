pipeline {
    agent none
      stages {
          stage('BuildingClinicalLabPod'){
              agent {
                label 'kubernetes_master'
            }
                steps {
                    sh 'sudo kubectl create deployment medportal  --image=sathya15/clinical_lab:v3   --kubeconfig /root/.kube/config'
                    sh 'sudo kubectl expose deployment medportal --type=NodePort  --port=4444   --kubeconfig /root/.kube/config'
                    sh 'sudo kubectl get pod -o wide   --kubeconfig /root/.kube/config'
                    
                }
        }
         stage('gettingpodinfo'){ 
             agent {
                label 'kubernetes_master'
            }
               steps {
                      sh 'sudo kubectl get pod -o wide  --kubeconfig /root/.kube/config'
                      sh 'sudo kubectl get svc    --kubeconfig /root/.kube/config'
             }
        }
    }
}
