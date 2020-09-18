---
title: "Fitness Functions"
date: 2020-09-14T21:10:59-05:00
tags: [Software Architecture, Evolutionary Architecture, OPA]
---

- Provide an **objective** way to assess a desired architectural characteristic
- Allow us to compare the software architecture before and after a change is introduced
- Amplify feedback loops by using metrics to guide future development

An example of fast feedback loop in which **pipelines can be modeled** to give developers feedback as quickly as possible.


# Fitness Function #1

| Name      |  Library |
| ----------- |  ----------- |
| **CIS Docker Benchmark**  | [conftest](https://github.com/open-policy-agent/conftest) |

{{< warning >}}
This is a code snippet to provide context and not a working example!
{{< /warning >}}

{{< code numbered="true" >}}
# policyconfig

run_as_required: true
approved_base_image_not_required: false
approved_base_images:
  - corpbaseimage
dockerfile_scanned_for_secrets: true
packages_verified: true

{{< /code >}}


```rego

package main
import cvepolicyconfig

deny[msg] {
    not user_defined
    msg = "<Architecture Code #1> Ensure a user for the container has been created."
}

user_defined {
    input[1].Cmd == "user"
}

user_defined {
    policyconfig.run_as_user_required == false
    trace("<Architecture Code #1> USER not required (set in .policyconfig)")
}

warn[msg] {
  not images_scanned_and_rebuilt_not_patched
  msg = "<Architecture Code #2> Ensure images are scanned and rebuilt to include security patches"
}

images_scanned_and_rebuilt_not_patched {
  policyconfig.images_not_treated_as_immutable == false
  trace("<Architecture Code #2> Images are immutable and continuously scanned for cve (set in .policyconfig)")
}

warn[msg] {
  not secrets_not_permitted_in_dockerfile
  msg = "<Architecture Code #3> Ensure secrets are not stored in Dockerfiles"
}

secrets_not_permitted_in_dockerfile {
  policyconfig.dockerfile_scanned_for_secrets == true
  trace("<Architecture Code #3> Commit hooks and routine repository scannng prevent secrets in Dockerfile (set in .policyconfig)")
}

```