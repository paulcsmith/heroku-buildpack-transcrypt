# heroku-buildpack-transcrypt
Make Heroku and transcrypt (elasticdog/transcrypt) play nicely with each other.

# Usage

Assuming you have a repo that you had set up with transcrypt and encrypted some files...

```bash
heroku config:set TRANSCRYPT_CMD="$(transcrypt -d | grep "transcrypt -c" | sed 's/^  //')"
heroku buildpacks:add --index 1 https://github.com/perplexes/heroku-buildpack-transcrypt
```

<3
