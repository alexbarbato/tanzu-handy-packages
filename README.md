# tanzu-handy-packages
A field maintained group of packages that can be installed on a Tanzu Application Clusters to make them all the more useful!

## Install and use
```bash
kubectl apply -f repo/package-repository.yml -n $(DESIRED-NAMESPACE)

# For each Package you desire run the following command for the relevant Package
# We recommend using the version constraint of >=0.0.0 which effectively equals latest unless there is a need otherwise.
tanzu package install tanzu-ai-accelerators -p tanzu-ai-accelerators.tanzuplatform.com -v ">=0.0.0" -n tap-install
```

For future updates you just need to update the `PackageRepository` and the subsequent `Packages` will automatically update.
```bash
kubectl apply -f repo/package-repository.yml -n $(DESIRED-NAMESPACE)
```

## Current `Packages`

### tanzu-ai-accelerators
A group of `Accelerators` maintained by the ML/AI TSL.

This set of `Accelerators` does require internet connectivity, the accelerators package from TAP on the cluster, and refers to GitHub.


## Developing `Packages`

1. Create a new directory with the `Package` name in the `./packages` directory
    1. Add a `config` directory where all relevant yaml will go.
2. Run the following to initialize the `Package`:
```bash
cd packages/YOUR-PACKAGE
kctrl package init
```
3. The version and release the `Package` as you see fit:
```bash
kctrl package release -v x.x.x --repo-output ../../repo
```
4. Finally publish the `PackageRepository`
```bash
cd ../../repo
kctrl package repository release
```