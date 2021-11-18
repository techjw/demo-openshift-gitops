# demo-openshift-gitops
Kubernetes manifests and instructions for deploying and managing OpenShift GitOps

### Install Operator
```oc apply -f gitops-operator-sub.yaml```

### Deploy Argo CD instance
1. Fork the SA-NE actions repository: https://github.com/sa-ne/openshift-github-actions
1. From the forked repo, click `Actions`
    * If this is your first use of actions, click the long green "I know what I'm doing" button to enable the feature.
1. Select the `deploy-argocd` action
1. Use the `Run workflow` drop down, giving the API endpoint of your OpenShift cluster.