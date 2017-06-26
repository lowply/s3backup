# s3backup

[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)][license]

[license]: https://github.com/lowply/lacrosse/blob/master/LICENSE

s3backup - A backup script using Amazon S3 as a storage.

## Usage

```bash
s3backup [ sync | test | clean ]
```

- `sync` will execute backup
- `test` will execute dryrun
- `clean` will remove all backups for the host

## Requirements

- macOS or Linux based platform
- awscli, jq
- aws profile granted S3 read/write permission

## Installation

Clone this repository and symlink `s3backup` to somewhere in your `$PATH`. For example:

```
git clone https://github.com/lowply/s3backup.git
ln -s $(pwd)/s3backup/s3backup /usr/local/bin/
```

## Config

Config is in JSON format. Here's an example:

```
{
    "enabled": true,
    "profile": "default",
    "bucket": "bucket",
    "dir": "backup",
    "node": "hostname",
    "exclude":[
        "*.DS_Store",
        "*Icon*",
        "*.cache/*",
        "*node_modules/*",
        "*vendor/*"
    ],
    "targets": [
        {
            "path": "/home",
            "exclude": [
                "*.cpanm/*",
                "*.gem/*",
                "*.github-backup-utils/*",
                "*.log/*",
                "*.node-gyp/*",
                "*.nodenv/*",
                "*.npm/*",
                "*.pyenv/*",
                "*.rbenv/*",
                "*.terminfo/*",
            ]
        },
        {
            "path": "/etc",
            "exclude": [
                "httpd/logs/*"
            ]
        }
    ]
}
```

## Logs

Logs will be recorded to the `~/.log/s3backup/YYMMDD.log` file.

## License

MIT

## Author

Sho Mizutani
