# deploy

This repository contains the deployment configuration for the kubernetes cluster and ArgoCD.

## ArgoCD

An example of ArgoCD port forwarding. You must specify the kubectl keys and know the argocd admin panel password.

`kubectl port-forward svc/argocd-server -n argocd 8080:443`


After that, ArgoCD will be available via the link https://127.0.0.1:8080 `Note: you need to use it without ssl or add the site as trusted in the settings`

## Continuous Delivery

Our continuous delivery uses **argoCD** and keeps track of the **"dev"** directory in the **"deploy"** repository. The development application configuration for **argoCD** is located at **deploy/dev/app.yaml**. Any changes made to the **dev** directory of the deploy repository will be reflected on the development server.

## Continuous Deployment

Our continuous deployment uses **argoCD** and keeps track of the **"prod"** directory in the **"deploy"** repository. The production application configuration for **argoCD** is located at **deploy/prod/app.yaml**. Any changes made to the prod directory of the deploy repository will be reflected on the production server, but unlike development server for added security, automatic initialization of synchronization is disabled on the production server. This means that to start a new synchronization, you need to click on the **"SYNC"** button in the argoCD client, or do it through the console.
