## なにこれ

- 長ったらしい、もしくは覚えにくいコマンドを Rake でラップするサンプル
- サンプルは aws-cli や docker コマンド、docker-compose コマンドをラッピングしている
- モチベーションについては[こちら](http://inokara.hateblo.jp/entry/2016/01/23/021142)

## 使い方

### Install

```sh
$ bundle
```

### Tasks

```sh
$ bundle exec rake -T
rake aws:create_repo     # Create repository
rake aws:describe_repos  # Describe repositories
rake aws:get_login       # Get login infomation
rake clean               # Remove any temporary products
rake clobber             # Remove any generated files
rake compose:ps          # Compose ps
rake compose:rm          # Compose remove
rake compose:stop        # Compose stop
rake compose:up          # Compose up with (-d) option
rake docker:build        # Build image
rake docker:login        # Login Repository
rake docker:push         # Push image
rake docker:tag          # Add tag
```
