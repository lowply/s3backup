# s3backup

[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)][license]

[license]: https://github.com/lowply/lacrosse/blob/master/LICENSE

s3backup - A backup script using Amazon S3 as a storage.

## Usage

```
s3backup [ sync | test | clean | size ]
```

## Requirements

- macOS or Linux based platform
- awscli, jq
- aws profile granted S3 read/write permission

## Installation

The install script will symlink s3backup to `~/bin`

```
git clone https://github.com/lowply/s3backup.git
cd s3backup && ./install
```

## Config

Config is in JSON format. Here's an example:

```
{
    "wifi_allow": [
        "Wifi SSID"
    ],
    "enabled": true,
    "profile": "default",
    "bucket": "bucket",
    "dir": "backup",
    "node": "hostname",
    "exclude":[
        "*.DS_Store",
        "*node_modules/*",
        "*vendor/*"
    ],
    "targets": [
        {
            "path": "/home",
            "exclude": [
                "*.rbenv/*",
            ]
        },
        {
            "path": "/etc/nginx",
            "exclude": [
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
