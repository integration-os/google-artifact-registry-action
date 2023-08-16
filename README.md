# google-artifact-registry-action

An action for GitHub Actions that authenticates to [Google Artifact Registry](https://cloud.google.com/artifact-registry), builds a Docker image and pushes it to an Artifact Registry repository.


## Usage

```yaml
jobs:
  build:
    name: Build and push Docker image to Google Artifact Registry
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: event-cloud/google-artifact-registry-action@v1
        with:
          image: us-east4-docker.pkg.dev/buildable-production/event-docker/my-service:v1
```

### Inputs

| Input  | Required? | Default | Description |
| ------ | --------- | ------- |------------ |
| `image`  | yes | | Full Docker image name to build and push, including the registry, repository and tag |
| `file` | no | `Dockerfile` | Path to the `Dockerfile` to build |
| `service_account` | no | `github-actions@buildable-production.iam.gserviceaccount.com` | GCP service account used to authenticate to Google Cloud |
| `workload_identity_provider` | no | `projects/157041665647/locations/global/workloadIdentityPools/github-actions/providers/github-actions` | GCP workload identity provider used to authenticate to Google Cloud |
