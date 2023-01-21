# Ansible deploy

### Deploy
```
ansible-playbook -i inventory deploy.yml --extra-vars "db_user=$DEV_DB_USER db_password=$DEV_DB_PASSWORD google_auth_secret=$DEV_GOOGLE_AUTH_SECRET build_id=$CI_PIPELINE_IID sms_api_key=$DEV_SMS_API_KEY"
```
sensistive data stored in CI and passed to ansible with `--extra-vars` flags

### Flow:
- create a new build dir
- copy compose and .env file to build dir
- create a symlink `build_latest` to the build dir
- run migrations
- run services

So you can keep versioning and easily switch between versions.