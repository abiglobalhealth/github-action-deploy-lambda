# GitHub Action to deploy a Lambda

## Introduction
This Action is to deploy a lambda to the environment provided, it first 
runs the tests and then deploys the lambda.

This Action runs the tests defined in the `package.json` command `test`.

## Variables
The action reads the following variables:
- environment: Environment in which the lambda will be deployed.
- node-version: Versión of Nodejs, default 16. 
- AWS_ACCESS_KEY_ID_DEV
- AWS_SECRET_ACCESS_KEY_DEV
- AWS_ACCESS_KEY_ID_TEST
- AWS_SECRET_ACCESS_KEY_TEST
- AWS_ACCESS_KEY_ID_PROD
- AWS_SECRET_ACCESS_KEY_PROD
- AWS_ACCESS_KEY_ID_CHINA
- AWS_SECRET_ACCESS_KEY_CHINA
- ABI_DATABASE_GATEWAY_DEPLOY_KEY: Deploy key to access the private repository.
- LIBBY_DEPLOY_KEY: Deploy key to access the private repository.

To access private repositories of Abi the `deploy` keys should be provided 
from `secrets`.

## Sample job

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: abiglobalhealth/github-action-deploy-lambda@v0.0.2
        with:
          environment: ${{github.event.inputs.environment}}
          node-version: 16
          AWS_ACCESS_KEY_ID_DEV: ${{secrets.AWS_ACCESS_KEY_ID_DEV}}
          AWS_SECRET_ACCESS_KEY_DEV: ${{secrets.AWS_SECRET_ACCESS_KEY_DEV}}
          AWS_ACCESS_KEY_ID_TEST: ${{secrets.AWS_ACCESS_KEY_ID_TEST}}
          AWS_SECRET_ACCESS_KEY_TEST: ${{secrets.AWS_SECRET_ACCESS_KEY_TEST}}
          AWS_ACCESS_KEY_ID_PROD: ${{secrets.AWS_ACCESS_KEY_ID_PROD}}
          AWS_SECRET_ACCESS_KEY_PROD: ${{secrets.AWS_SECRET_ACCESS_KEY_PROD}}
          AWS_ACCESS_KEY_ID_CHINA: ${{secrets.AWS_ACCESS_KEY_ID_CHINA}}
          AWS_SECRET_ACCESS_KEY_CHINA: ${{secrets.AWS_SECRET_ACCESS_KEY_CHINA}}
          ABI_DATABASE_GATEWAY_DEPLOY_KEY: ${{secrets.ABI_DATABASE_GATEWAY_DEPLOY_KEY}}
          LIBBY_DEPLOY_KEY: ${{secrets.LIBBY_DEPLOY_KEY}}
```