# AAP 2.5 - Provision GCP VM

## Requirements
- AAP 2.5 Project pointing to this repo
- Execution Environment with `google.cloud` collection (install via this repo's `ansible/requirements.yml`)
- GCP credentials:
  - Prefer an AAP Credential of type "Google Compute Engine" (Service Account)
  - Or set env var `GOOGLE_APPLICATION_CREDENTIALS` to a JSON key in the EE

## Variables
- `project_id` (required) or env `GCP_PROJECT`
- `zone` (default: `us-central1-a`)
- `instance_name` (default: `example-vm`)
- `machine_type` (default: `e2-medium`)
- `disk_size_gb` (default: `20`)
- `source_image` (default latest Debian 12 family)
- `network` (default: `default`)
- `subnetwork` (optional)
- `assign_external_ip` (default: `true`)
- `preemptible` (default: `false`)
- `labels`, `tags`

## Run locally (optional)
```bash
ansible-galaxy collection install -r ansible/requirements.yml
ansible-playbook ansible/playbooks/provision_gcp_vm.yml -e project_id=$GCP_PROJECT
```

## AAP Job Template
- Inventory: `localhost`
- Playbook: `ansible/playbooks/provision_gcp_vm.yml`
- Credentials: your GCP Service Account credential
- Extra Vars (example):
```yaml
project_id: your-gcp-project-id
zone: us-central1-a
instance_name: demo-aap-vm
machine_type: e2-standard-2
labels:
  owner: aap
  purpose: demo
```
