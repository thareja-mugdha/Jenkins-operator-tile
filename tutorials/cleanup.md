---
title: Jenkins Operator cleanup Tutorial
description: This tutorial explains how to cleanup Operator
---


### Cleaning Up Operator

**Delete the operator's CRs by kubectl delete commands :**

 ```copycommand
 kubectl delete -f jenkins-instance.yaml -n my-jenkins-operator
 ```

**Delete the operator by kubectl delete command:**

 ```copycommand
 kubectl delete -f https://operatorhub.io/install/jenkins-operator.yaml
 ```

**Delete all the yaml files:**

  ```copycommand
  rm -rf jenkins-instance.yaml
  ```

  Similarly, you can delete rest of yaml files.

