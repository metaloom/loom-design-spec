# Pipeline

**Pipelines** are used to define automatic **Asset** and **Content** processing.

## Concept / Usecase

A pipeline consists of multiple nodes which can be connected via the UI by the user. A pipeline might scan a folder and process new assets by hashing and filtering them.

TODO: Decide how to use pipelines for **Contents**.

## Node Types

### Source

Node which provides a stream of assets

* From Collection
* From Tag
* From Folder / Scan Folder
* From Asset
* From Content?

### Filter

Filters the pipeline (e.g. has two output nodes)

* Filter - Can be used to filter assets by name, size, meta properties, regex
* Geo Fence Filter - Filter asset by using the Geo information

### Action

Modifies the output (one output node)

* Thumbnail Generator Action - Generate a thumbnail of the media
* Fingerprint Action - Generate Media Fingerprint of the asset
* Dominant Color Action - Generate the dominant color information
* Geo Fence Action - Modify the asset by using the Geo information
* PDF Converter Action - Convert the asset to PDF
* Review Action - Assigns the Asset to a user for review
* Event Action - Dispatches a custom event
* Lua Action - Invokes a LUA script
* Groovy Action - Invokes a Groovy script
* Mail Action - Dispatches a mail
* Assign to Collection Action
* Auto Tag Action - Automatically adds tags to the media by using a configured regex filter
* Hash Action - Hashes the asset via SHA512, SHA256, MD5
* Upload Action - Upload the asset somewhere (e.g. S3)
* S3 Action - Copy or move the asset via S3 API
* Webhook Action - Invokes external API
* Image Annotation Action - Uses machine learning / ML API to add annotations to the media.

## Node Properties

* Name - Name of the node
* Type - Type of the node
* Abort on error - Whether to abort processing if an error occurs. Otherwise the next node is invoked.
* Invoke Next - Whether to continue processing
* Parallel - Whether to process the stream in-parallel

Read Only:
* Processed Items
* Total running time

## Requirements

- Support for asset fingerprinting
- Support for asset thumbnail generation


