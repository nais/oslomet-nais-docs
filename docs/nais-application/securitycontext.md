---
description: Kubernetes security context for containers
---

# Container security context
Kubernetes restricts the capabilities of containers by using `SecurityContext` settings. This feature advances the security in the pods running on Kubernetes.

By default we set the following `securityContext` for the application container:
```yaml
securityContext:
  runAsUser: 1069
  runAsGroup: 1069
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  runAsNonRoot: true
  privileged: false
  capabilities:
    drop: ["all"]
```

## Enable specific kernel capabilities

Enable specific kernel capabilities by adding the following annotation to your `Application` or `NaisJob` spec:
```yaml
apiVersion: nais.io/v1alpha1
kind: Application
metadata:
  annotations:
    nais.io/add-kernel-capability: "NET_RAW"
```

The annotation supports multiple values separated by comma. 
Not all capabilities are supported, so if you encounter issues with missing capabilities contact the nais team.

A list of capabilities can be found [here](https://steflan-security.com/linux-privilege-escalation-exploiting-capabilities/)

## Relevant information
[Configure security context](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)

[Docker security best practices](https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html#rule-3-limit-capabilities-grant-only-specific-capabilities-needed-by-a-container)