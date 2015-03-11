# ansible-rds-ca-bundle

An Ansible role for installing the [Amazon Relational Database Service (RDS)](http://aws.amazon.com/rds/) certificate bundle.

## Role Variables

- `rds_ca_bundle_url` - URL for the RDS CA bundle (default: `http://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem`)

## Example Playbook

After installing the Amazon RDS CA bundle, use the following commands to confirm that the installation completed successfully:

```bash
$ export PGSSLROOTCERT="/etc/ssl/certs/ca-certificates.crt"
$ export PGSSLMODE="verify-full"
$ psql -h <DB_ENDPOINT> -U <DB_USER>
```

**Note**: This test is specifically targeted at an RDS PostgreSQL instance.

If you are met with the following error message, then either the installation did not complete successfully, or you do not have a matching certificate authority associated with your Amazon RDS PostgreSQL instance:

```
psql: SSL error: certificate verify failed
```

For more details, see the [examples](./examples/) directory.
