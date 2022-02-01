# Asset

## Properties

* Retention?
* Content Disposition
* Content Type
* Content Language
* Content Encoding
* MD5, SHA512, SHA256
* Owner, Creation Date, ID
* Update Date
* Meta Attributes

## Asset lifecyle:

* 1: Upload -> Asset
* 2: Place locally -> Create Asset -> Asset
* 3: Upload to S3  -> Create Asset -> Asset
* 4: S3 Event? -> Extension -> Create Asset -> Asset (download, presignedUrl, download redirect, s3 link rendering)

## Requirements