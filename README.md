# WebHosting-on-AliyunFC
Run most of the websites written by PHP on Aliyun Function Compute without any changes.

## Usage
* Fork this repo.
* Edit tinyfilemanager/index.php, change "auth_users" username&password, and other configs if you like.
* Login to Aliyun Console:
  * Create a VPC and vSwitch.
  * Create a NAS on the same region.
  * Create a Service on the same region.
  * Edit the service, attach created NAS to it, and modify the Role which the service will use.
  * Create a Funtion belong to the service, choose custom runtime.
  * Export the function configurations from the fc console, save it to `template.yml`.
  * Add `CodeUri: ./` to function properties in `template.yml`, save and upload it to somewhere(Github Gist is a good choice).
* Edit `config/vhost/main.conf` in advance.
* Add secrets:
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
* Trigger actions, wait it to finish.
* Add custom domain at console.
* Upload your website files via tinyfilemanager.