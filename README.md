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

## Current Packages

### tanzu-ai-accelerators
A group of accelerators maintained by the ML/AI TSL.

This set of accelerators does require internet connectivity and refers to GitHub.

