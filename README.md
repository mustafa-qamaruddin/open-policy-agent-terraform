# Unit Testing Terraform Plan with Open Policy Agent (OPA)

Unit testing for Infrastructure as Code helps avoid applying unintended changes to the production environment. You Only Look Once (YOLO) terraform apply could lead to undesired consequences in production environment. Unit testing with OPA helps automate terraform apply and avoid unintedned changes.

```
 terraform init
 terraform plan --out tfplan.binary 
 terraform show -json tfplan.binary > tfplan.json
 opa exec --decision terraform/analysis/authz --bundle policy/ tfplan.json
 opa exec --decision terraform/analysis/score --bundle policy/ tfplan.json
```

Reference: [Open Policy Agent - Terraform](https://www.openpolicyagent.org/docs/latest/terraform/)