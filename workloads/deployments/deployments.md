# Deployments

Hello!

A deployment is an instance that automatically will create a Pod and a ReplicaSet.

In a deployment we set a `Desired State` and the `Deployment Controller` will be in charged of reaching that state.

Once that we have created a Deployment, we will see the following

First, run the apply command from the nginx folder:

    kubectl apply -f nginx-deployment.yaml

If then we run:

    kubectl get all

We will see the following:

    NAME                                    READY   STATUS    RESTARTS   AGE
    pod/nginx-deployment-5bddfff64f-2fzdj   1/1     Running   0          5s
    pod/nginx-deployment-5bddfff64f-jx5vw   1/1     Running   0          5s
    pod/nginx-deployment-5bddfff64f-kffqq   1/1     Running   0          5s

    NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
    deployment.apps/nginx-deployment   3/3     3            3           5s

    NAME                                          DESIRED   CURRENT   READY   AGE
    replicaset.apps/nginx-deployment-5bddfff64f   3         3         3       5s

As we can see, we have three pods, a deployment and a replicaset.


### Labels

As you can see in the `nginx-deployment.yaml` file, we have multiple labels.

The ones within the metadata, are just reference for the Deployment.

The ones under `spec.template.metadata.labels` refers to the labels of the Pods and ReplicaSet itself. The `spec.selector.matchLabels` refers to the selectots, meaning that the replicaset will handle the pods with that label. So, the Pod and the ReplicaSet should have the same label.

## Rolling back

There are times when we modify the deployments, and sometimes we will need to rollback to some previous version. To get the versions we can run:

    kubectl rollout history deployment/nginx-deployment

And we will get the following output:

    deployment.apps/nginx-deployment 
    REVISION  CHANGE-CAUSE
    1         <none>
    2         <none>

The versions will depend on how many versions we do have.

To check a specific version, we can run:

    kubectl rollout history deployment/nginx-deployment --revision=2

And get the output with the description of that revision.

If we made some error and we want to go back to an older revision, we can do it like this:

    kubectl rollout undo deployment/nginx-deployment

Adittionaly, we can specify the revision that we want to restore

    kubectl rollout undo deployment/nginx-deployment --to-revision=2