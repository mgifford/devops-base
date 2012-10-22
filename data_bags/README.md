Encrypted Data Bags Support
===========================

Sensitive information can be passed by using Encrypted Data Bags.

The knife command for creating encrypted data bags doesn’t work well without a Chef server, so use this [This gist](https://gist.github.com/2896172) as an example on how to create encrypted data bag items on your local file system.

This gist has been implemented using the command 'rake databags [context]' the password has been removed for security.

The data bag key was generated with the following command: 'openssl rand -base64 512 | tr -d '\r\n' > data_bag_key'