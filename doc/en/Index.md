# SphinxID - Basic Documentation

## Overview

SphinxID is designed to securely manage anonymous identifiers for research participants, especially in sensitive fields like health and social sciences. It replaces insecure Excel-based association files with a robust, auditable system built on Hashicorp Vault.

### Key Features

- Researchers can declare associations between participants and research codes, but cannot view these associations.
- Only the Data Protection Officer (DPO) can access associations, and only for individual unmasking.
- All secrets and operations are securely stored and logged in Vault.
- SphinxID acts as a configuration and query interface for Vault.
- **Access rights are strictly defined by Vault policies and are tamper-proof.**
- **All actions are logged and cannot be altered, ensuring full traceability and auditability.**

## Main Concepts

### Instances

- Each organization (school, university, etc.) is an Instance.
- Instances are created from the ROR registry.
- Each instance has at least one administrator and one DPO.
- Authentication is via LDAP, SAML, or OIDC.

### LDAP Authentication

- Supports authenticated and anonymous bind modes.
- Real-time feedback on LDAP configuration and compatibility.

### Laboratories

- Administrators define one or more labs per instance.
- Each lab can have multiple researchers.

### Projects

- Researchers define projects within labs.
- Projects can specify secret generation rules (manual, sequence, random).

### Secrets

- Researchers enter [key, secret] pairs for each project.
- Secret rules are project-specific and can be manual, sequential, or random.

## Data Architecture

- All data is stored under a root path (e.g., `sphinxIDVXX`) in Vault.
- Global instance list: `/globaldata/.instances`
- Instance data: `/[instanceCode]/.instance-info`
- Labs: `/[instanceCode]/labs/[labCode]/lab-info`
- Projects: `/[instanceCode]/labs/[labCode]/projects/[projectCode]/project-info`
- Secrets: `/[instanceCode]/labs/[labCode]/projects/[projectCode]/secrets/[key]`

## Example Workflow

1. Researcher enters participant info and anonymous ID in SphinxID.
2. Data is encrypted and stored in Vault.
3. Only the DPO can access the association if needed.

Let's really protect our secrets!