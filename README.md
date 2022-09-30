# download-artifact-gh-action

This action will recursively download and unzip a folder from s3 bucket containing your service artifact(s). Here is an example on how to use it:

```yaml
env:
  REGION: "eu-west-1"

jobs:
  download-artifacts:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: ohpensource/download-artifact-gh-action@main
        name: Download all artifacts for deployment
        with:
          region: $REGION
          access-key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          secret-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          account: "account id where the s3 bucket is located"
          role-name: "your role name"
          version: "v0.0.1"
          service-name: "your service name"
          iac: "iac zip file to unzip. Regex build base on *-$iac.zip"
          bucket-name: "artifact name"
          destination-folder: "deployment-folder"
```

# License Summary

This code is made available under the MIT license. Details [here](LICENSE).
