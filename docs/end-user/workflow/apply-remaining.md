---
title:  Apply Remaining
---

## Overview

If we have applied some resources and do not want to specify the rest one by one, KubeVela provides the `ApplyRemaining` workflow step to filter out selected resources and apply remaining.

In this guide, you will learn how to apply remaining resources via `ApplyRemaining` in WorkflowStepDefinition.

## Apply Base Definitions

```yaml
apiVersion: core.oam.dev/v1beta1
kind: Application
metadata:
  name: first-vela-workflow
  namespace: default
spec:
  components:
  - name: express-server
    type: webservice
    properties:
      image: crccheck/hello-world
      port: 8000
    traits:
    - type: ingress
      properties:
        domain: testsvc.example.com
        http:
          /: 8000
  workflow:
    steps:
      - name: express-server
        type: apply-remaining
        properties:
          exceptions:
            express-server:
              skipApplyWorkload: false
              skipAllTraits: false
              skipApplyTraits:
                - ingress

---
apiVersion: core.oam.dev/v1beta1
kind: WorkflowStepDefinition
metadata:
  name: apply-remaining
spec:
  schematic:
    cue:
      template: |
        import ("vela/op")
        parameter: {
            exceptions?: [componentName=string]: {
              // skipApplyWorkload indicates whether to skip apply the workload resource
              skipApplyWorkload: *true | bool

              // skipAllTraits indicates to skip apply all resources of the traits.
              // If this is true, skipApplyTraits will be ignored
              skipAllTraits: *true| bool

              // skipApplyTraits specifies the names of the traits to skip apply
              skipApplyTraits: [...string]
           }
        }

        apply: op.#ApplyRemaining & {
          parameter
        }
```

## Expected outcome

We can see that the component have been applied to the cluster, but the trait named ingress has been skipped.

With `ApplyRemaining`, we can easily filter and apply resources by filling in the built-in parameters.