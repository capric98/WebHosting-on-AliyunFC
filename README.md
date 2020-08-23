# WebHosting-on-AliyunFC
Run most of the websites written by PHP on Aliyun Function Compute without any changes.

## Usage
1. Fork this repo.
2. Edit tinyfilemanager/index.php, change "auth_users" username&password, and other configs if you like.
3. Login to Aliyun Console:
  * Create a VPC and vSwitch.
  * Create a NAS on the same region.
  * Create a Service on the same region.
  * Edit the service, attach created NAS to it, and modify the Role which the service will use.
  * Create a Funtion belong to the service, choose custom runtime.
  * Export the function configurations from the fc console, save it to `template.yml`.
  * Add `CodeUri: ./` to function properties in `template.yml`, save and upload it to somewhere(Github Gist is a good choice).
4. Edit `config/vhost/main.conf` in advance.
5. Add secrets:
  * TEMPLATE_URL: Actions will download template.yml from this URL.
  * REGION: Aliyun FC Region
  * ACCOUNT_ID: Aliyun Account ID
  * ACCESS_KEY_ID: Aliyun ACCESS_KEY_ID
  * ACCESS_KEY_SECRETS: ACCESS_KEY_SECRETS

    **Ps.  Make sure that your RAM Role has the following privileges:**
    * AliyunRAMFullAccess
    * AliyunNASFullAccess
    * AliyunFCFullAccess
    * AliyunECSNetworkInterfaceManagementAccess
6. Trigger actions, wait it to finish.
7. Add custom domain at console.
8. Upload your website files via tinyfilemanager.