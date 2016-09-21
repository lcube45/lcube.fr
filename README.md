# lcube.fr
Drupal 8 Proof of concept !

Day 1
-----

Git workflow
http://nvie.com/posts/a-successful-git-branching-model/

Drupal console
https://hechoendrupal.gitbooks.io/drupal-console/content/en/index.html

```shell
$ drupal chain --file==install.yml
```

```yaml
commands:
# Download Drupal
  - command: site:new
    arguments:
      directory: 'lcube.dev'
    options:
      latest: 'true'
# Install Drupal
  - command: site:install
    options:
      langcode: 'fr'
      db-type: '%{{db_type|mysql}}'
      db-host: '%{{db_host|127.0.0.1}}'
      db-name: '%{{db_name|lcube.dev}}'
      db-user: '%{{db_user|}}'
      db-pass: '%{{db_pass}}'
      db-port: '%{{db_port|3306}}'
      site-name: 'lcube.dev'
      site-mail: 'info@lcube.fr' # default email
      account-name: 'lcube' # default account
      account-mail: 'info@lcube.fr' # default email
      account-pass: '' # default pass
    arguments:
      profile: 'minimal'
# Start php built-in server
  - command: server
```