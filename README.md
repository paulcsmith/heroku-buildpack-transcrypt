# heroku-buildpack-transcrypt

Decrypt your transcrypt-encrypted files on deploy.

# Best practices

Rails now has a secrets.yml, which is actually some ERB that can grab variables out of your ENV. [Setting environment variables on Heroku](https://devcenter.heroku.com/articles/config-vars) is the recommended way for passing secrets.

However in some situations you need to put secrets into [app.json](https://devcenter.heroku.com/articles/app-json-schema) like if you're driving deploys via API. This is a good file to encrypt.

Other good files to encrypt are SSL certificates, and API keys that libraries use that you can't modify to use environment variables.

# Usage

Assuming you have a repo that you had set up with transcrypt and encrypted some files...

```bash
heroku config:set TRANSCRYPT_CMD="$(transcrypt -d | grep "transcrypt -c" | sed 's/^  //')"
heroku buildpacks:add --index 1 https://github.com/perplexes/heroku-buildpack-transcrypt
```

<3
