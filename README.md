# demo-openshift-gitops
Kubernetes manifests and instructions for deploying and managing OpenShift GitOps

### Install Operator
```oc apply -f gitops-operator-sub.yaml```

### Deploy Argo CD instance
1. Fork the SA-NE actions repository: https://github.com/sa-ne/openshift-github-actions
1. Follow the [README](https://github.com/techjw/openshift-github-actions#how-to-use) setup your fork.
    * Also, create the `OC_USER` and `OC_PASSWORD` secrets in your forked repo.
1. From the forked repo, click `Actions`
    * If this is your first use of actions, click the long green "I know what I'm doing" button to enable the feature.
1. Select the `deploy-argocd` action
1. Use the `Run workflow` drop down, giving the API endpoint of your OpenShift cluster.
    * The Action should take less than 3 minutes, but the job may take 8-10 minutes to complete.
1. Login to the OpenShift console, confirm that the OpenShift GitOps operator shows 2 Instances:
    * ArgoCD: `openshift-gitops`
    * AppProject: `default`
1. If the instances do not appear right away, check for resources in project `openshift-gitops` and give the operator a minute or so to catch up.

### Open Argo CD console
1. From `Installed Operators` > `Red Hat OpenShift GitOps` > `All instances`: click on the ArgoCD instance `openshift-gitops`
1. Switch to the `Resources` view, select the `Route` named `openshift-gitops-server`
1. Click to open the listed `Location` URL

**-- OR --**

1. From the CLI, run: `oc get route openshift-gitops-server -n openshift-gitops`
1. Copy the HOST/PORT and open in a browser
