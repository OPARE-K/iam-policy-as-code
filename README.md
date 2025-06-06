# 🛡️ IAM Policy as Code with Terraform & GitHub Actions

This project demonstrates how to manage AWS IAM policies as code using **Terraform**, and deploy them automatically via **GitHub Actions** CI/CD workflows.

---

## 📁 Project Structure

iam-policy-as-code/
├── terraform/
│ ├── main.tf
│ ├── variables.tf
│ ├── outputs.tf
│ └── iam-policy.json
└── .github/
└── workflows/
└── deploy.yml


---

## 🚀 Features

- 🧱 **Terraform Infrastructure as Code** for AWS IAM policy
- ⚙️ **CI/CD Pipeline** using GitHub Actions
- 🔐 **Secure AWS authentication** with GitHub Secrets
- ✅ Auto-run `terraform fmt`, `validate`, `plan`, and `apply` on push
- 🧪 Built-in formatting and validation checks for Terraform code

---

## ⚙️ How It Works

1. You push code to the `main` branch.
2. GitHub Actions triggers the workflow.
3. The workflow:
   - Checks out the code
   - Installs Terraform
   - Runs formatting and syntax checks
   - Plans and applies IAM policies to AWS using Terraform

---

## 🔐 AWS Credentials (Security)

Secrets are securely stored in GitHub:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

These are passed as environment variables to the GitHub Actions runner and **never hardcoded**.

---

## 📦 Files Explained

| File                        | Purpose                                             |
|----------------------------|-----------------------------------------------------|
| `main.tf`                  | Defines the Terraform resources (IAM policy)       |
| `iam-policy.json`          | Contains the actual IAM policy in JSON format      |
| `variables.tf`             | (Optional) Defines input variables                 |
| `outputs.tf`               | (Optional) Outputs results after apply             |
| `deploy.yml`               | GitHub Actions workflow file                       |

---

## 🛠️ Setup Instructions

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/iam-policy-as-code.git

# Navigate to the terraform directory
cd iam-policy-as-code/terraform

# Initialize Terraform
terraform init

# Run plan/apply locally (optional)
terraform plan
terraform apply

To run the CI/CD:

    Push changes to main

    The GitHub Actions pipeline will handle the rest

✅ Example IAM Policy (iam-policy.json)

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "ec2:DescribeInstances"
      ],
      "Resource": "*"
    }
  ]
}

📌 GitHub Actions Workflow

Located at .github/workflows/deploy.yml, it automates the full Terraform flow: fmt → validate → plan → apply.
💡 Lessons Learned

    GitHub’s 100MB file limit must be handled by ignoring .terraform/

    Always use .gitignore and never commit provider binaries

    IAM should be managed as code for compliance and auditability

    Secrets must be used, not hardcoded credentials

📚 Future Improvements

    🔄 Use GitHub OIDC to authenticate to AWS (no long-term secrets)

    🌍 Add remote backend (e.g., S3 + DynamoDB for state locking)

    🧪 Add Terraform testing tools (e.g., tflint, terraform-compliance)

    🏗️ Add dev/stage/prod environments

🔗 Related Skills

    Terraform

    GitHub Actions

    AWS IAM

    DevSecOps / GitOps

    Infrastructure as Code (IaC)

👨‍💻 Author

 Name - K.Opare
