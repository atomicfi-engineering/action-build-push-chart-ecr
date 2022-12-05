<!-- start title -->

# GitHub Action:Build and Push Chart to ECR

<!-- end title -->
<!-- start description -->

Builds and pushes a chart to an ECR repository

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: atomicfi-engineering/action-composite-action-template@undefined
  with:
    # Path to the chart to build and push. Required.
    # Default:
    chart-path: ""
    # Name of ECR repository to push the chart to
    # Default: charts
    ecr-repository: ""
    # AWS secret key ID. Required.
    # Default:
    aws-access-key-id: ""
    # AWS secret access key. Required.
    # Default:
    aws-secret-access-key: ""
    # AWS region. Required.
    # Default:
    aws-region: ""
    # AWS IAM role to assume.
    # Default:
    role-to-assume: ""
    # AWS IAM role external id
    # Default:
    role-external-id: ""
    # AWS IAM role assumption duration seconds
    # Default: 900
    role-duration-seconds: ""
    # AWS IAM role assumption session name
    # Default: action-build-push-chart-ecr
    role-session-name: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**                   | **Description**                             | **Default**                   | **Required**  |
| :-------------------------- | :------------------------------------------ | :---------------------------: | :-----------: |
| **`chart-path`**            | Path to the chart to build and push         |                               |   **true**    |
| **`ecr-repository`**        | Name of ECR repository to push the chart to | `charts`                      |   **false**   |
| **`aws-access-key-id`**     | AWS secret key ID                           |                               |   **true**    |
| **`aws-secret-access-key`** | AWS secret access key                       |                               |   **true**    |
| **`aws-region`**            | AWS region                                  |                               |   **true**    |
| **`role-to-assume`**        | AWS IAM role to assume.                     |                               |   **false**   |
| **`role-external-id`**      | AWS IAM role external id                    |                               |   **false**   |
| **`role-duration-seconds`** | AWS IAM role assumption duration seconds    | `900`                         |   **false**   |
| **`role-session-name`**     | AWS IAM role assumption session name        | `action-build-push-chart-ecr` |   **false**   |
    
<!-- end inputs -->
<!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
<!-- start examples -->

### Example usage

```yaml
on:
  push:
    branches:
      - main
jobs:
  build-and-push-helm-chart-to-ecr:
    runs-on: ubuntu-latest
    name: Build and Push Helm Chart to ECR
    steps:
      - uses: atomicfi-engineering/action-build-push-ecr@v1.0.0
        with:
          chart-path: charts/chart-name
          ecr-repository: charts
          aws-access-key-id: ${{ secrets.AUTOMATION_AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AUTOMATION_AWS_SECRET_ACCESS_KEY }}
          role-to-assume: arn:aws:iam::000000000000:role/YourRoleHere
          aws-region: us-west-2
          extra-account-access: 000000000000,111111111111,222222222222
```

<!-- end examples -->