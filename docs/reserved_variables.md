# Reserved Variables

There are specific environment variables that are reserved for certain use-cases.

## SSH Private Keys for Private Git Repository Package Access

`GIT_SSH_PRIVATE_KEY` is a reserved variable that should be set if you have private repository packages.

> The following instruction and example is secrets encryption for Alpha which will be deprecated in Beta.

To encrypt, set the ssh private key env variable into your `.env` file as-is in the private key file with single quotes
around them.

Example `.env` file to be encrypted:
```
GIT_SSH_PRIVATE_KEY='-----BEGIN OPENSSH PRIVATE KEY-----
therearelotsofprivatekeymaterialhere
onvariouslineslikethis
wecanjustcopypasteasitappearsinthefile
andusesinglequotesaroundthewholething
-----END OPENSSH PRIVATE KEY-----'
SOME_OTHER_SECRET=1234asdf
```

Then continue with encryption using the [kms-ext](https://github.com/meltano/kms-ext) utility.

## Job or Schedule Run Notifications via Webhook

`MELTANO_CLOUD_WEBHOOK_URL` can be set to receive notifications on success or fail of a job or schedule run.

Currently only one webhook url can be configured.
