These manifest files are specifically designed for the Development Preview of OpenShift 4.16 at Oracle Cloud Compute@Customer(C3). They are used in the step: "Custom manifests", of provisioning an OpenShift cluster in RedHat's Hybrid Cloud Console / OpenShift UX.

`cloud-provider.yaml` in `oci-ccm.yml` and `config.yaml` in `oci-csi.yml` should be replaced by the output from running the `createInfraResources.tf` file.

example:
```
stringData:
  cloud-provider.yaml: |
    useInstancePrincipals: true
    compartment: <compartment-ocid>
    vcn: <vcn-ocid>
    loadBalancer:
      subnet1: <subnet-ocid>
      securityListManagementMode: Frontend
      securityLists:
        <subnet-ocid>: <security-ocid>
    rateLimiter:
      rateLimitQPSRead: 20.0
      rateLimitBucketRead: 5
      rateLimitQPSWrite: 20.0
      rateLimitBucketWrite: 5
```


`oci-ccm-C3-cert.yaml` in `oci-ccm.yml` should be replaced by the C3 cert.

example:
```
stringData:
  scasg03-cert.pem: |
    -----BEGIN CERTIFICATE-----
    your cert content
    -----END CERTIFICATE-----

```