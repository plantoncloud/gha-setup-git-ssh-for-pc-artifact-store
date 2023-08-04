# GitHub Action: Setup Git SSH for Planton Cloud Artifact Store (gha-setup-git-ssh-for-pc-artifact-store)

This GitHub Action (gha-setup-git-ssh-for-pc-artifact-store) configures Git to use SSH for accessing private Go packages hosted on GitHub or GitLab. It uses an SSH key fetched from a Planton Cloud Artifact Store and configures Git and SSH to use this key, providing seamless and secure access to your private Go packages during your build process.

## Inputs

This action requires one input:

- `planton_cloud_artifact_store_id`: The ID of the Artifact Store on Planton Cloud from where the Git SSH key can be fetched.

## Usage

Include this action in your GitHub workflow file as shown below:

```yaml
steps:
  - name: Setup Git SSH
    uses: your-github-username/gha-setup-git-ssh-for-pc-artifact-store@main
    with:
      planton_cloud_artifact_store_id: 'your-artifact-store-id'
```

## Example of a Complete Workflow

This action is usually used as part of a larger workflow, which includes other steps such as checking out the code, building the Go application, and pushing the resulting Docker image. Here is an example of how to use this action in a complete workflow:

```yaml
name: Build and Deploy Go Application

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Setup Git SSH
      uses: your-github-username/gha-setup-git-ssh-for-pc-artifact-store@main
      with:
        planton_cloud_artifact_store_id: 'your-artifact-store-id'

    - name: Build Go application
      run: make build

    - name: Push Docker image
      run: |
        echo "pushing Docker image..."
        # add your Docker push commands here
```

## Contributing

If you have suggestions for how this GitHub Action could be improved, or want to report a bug, open an issue! We'd love all and any contributions.

## License

This project is licensed under the [MIT License](LICENSE).
