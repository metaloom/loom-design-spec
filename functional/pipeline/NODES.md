# Nodes

List of pipeline node types

## Source Nodes

### From Collection

Create a stream from all assets that belong to a collection

```json
{
    "id": "source-by-collection",
    "collection": ["summer-photos", "winter-photos"], // Collections to source assets from
    "next": ["<next-node>"]
}
```

### From Tag

Create a stream from all assets that are tagged

```json
{
    "id": "source-by-tag",
    "tags": ["red", "green", "blue"], // Tags to source assets from
    "next": ["<next-node>"]
}
```

### From Folder

Create a stream from a folder

```json
{
    "id": "source-by-fs",
    "folder": "<filesystem-path>",
    "next": ["<next-node>"]
}
```

### From Asset

Create a stream from asset/s.

```json
{
    "id": "source-by-asset",
    "asset": "<reference-to-asset>", // UUIDs of the assets
    "next": ["<next-node>"]
}
```

### From Content

Create a stream from content/s.

```json
{
    "id": "source-by-content",
    "content": "<reference-to-content>", // UUIDs of the contents
    "next": ["<next-node>"]
}
```

## Filter Nodes

_Filters the pipeline (e.g. has two output nodes)_

### Property Filter

Can be used to filter assets by name, size, meta properties, regex.


```json
{
    "id": "property-filter",
    "size-range-max": "100MB",
    "size-range-min": "10MB",
    "name-regex": "<regex-for-assetname>",
    "pass": ["…"],
    "reject": ["…"]
}
```

### Geo Fence

Filter asset by using the Geo information.

```json
{
    "id": "filter-by-area",
    "area": […], // Geo Area (user can choose it on a map)
    "pass": ["…"], // Node to be invoked for passed elements
    "reject": ["…"] // Node to be invoked for rejected elements
}
```

### Whitelist / Blacklist

Whitelist/blacklist assets by hash or fingerprint.

```json
{
    "id": "whitelist-filter",
    "whitelistRef": ["…"],
    "blacklistRef": ["…"],
    "mode": "blacklist", // Whitelist / Blacklist mode
    "pass": ["…"],
    "reject": ["…"]
}
```
## Meta? Node

### Assign to Collection Action

Assigns the asset to a collection based on meta information

Format
```json
{ 
    "id": "assign-to-raw",
    "collection":  "raw", // Collection to assign to asset to
    "next": ["<next-node>"]
}
```

### Review Action

Assigns the Asset to a user for review

```json
{
    "id": "assign-to-joe",
    "user": "joeDoe",
    "next": ["<next-node>"]
}
```

### Event Action

Dispatches a custom event

### Lua Action

Invokes a LUA script

```json
{
    "id": "run-script",
    "script": "<LUA Script>",
    "next": ["<next-node>"]
}
```


### Groovy Action

Invokes a Groovy script

```json
{
    "id": "run-script",
    "script": "<Groovy Script>",
    "next": ["<next-node>"]
}
```

### ~~Mail Action~~

~~Dispatches a mail~~

TODO: Maybe this should better be handled via webhook as it requires templates and net access.

### Auto Tag Action
Automatically adds tags to the media by using a configured regex filter

### Webhook Action

Invokes external API

```json
{
    "id": "invoke-api",
    "endpoint": "URL to endpoint",
    "next": ["<next-node>"]
}
```

## Worker Node

_Runs IO intensive operations_

### Image Annotation Action

Uses machine learning / ML API to add annotations to the media.

### PDF Converter Action

Convert the asset to PDF

```json
{
    "id": "convert-to-pdf",
    "qualityFactor": 0.90, 
    "next": ["<next-node>"]
}
```

### Thumbnail Generator Action

Generate a thumbnail of the media

```json
{
    "id": "generate-thumbnail",
    "cols": 2,
    "rows": 2,
    "tileSize": 512,
    "next": ["<next-node>"]
}
```

### Fingerprint Action

Generate Media Fingerprint of the asset


```json
{
    "id": "fingerprint",
    "algo": "v3",
    "next": ["<next-node>"]
}
```

### Dominant Color Action

Generate the dominant color information


```json
{
    "id": "extract-dominant-color",
    "next": ["<next-node>"]
}
```

### Hash Action 

Hashes the asset via SHA512, SHA256, MD5

```json
{
    "id": "hash",
    "md5": true,
    "sha256": true,
    "sha512": true,
    "next": ["<next-node>"]
}
```

### S3 Action

Copy or move the asset via S3 API

### Upload Action

Upload the asset somewhere (e.g. S3)

### Filesystem Action

Moves, Deletes, Copies assets

```json
{
    "id": "fs-operation",
    "targetFolder": "/tank/assets",
    "copy": false,
    "move": true,
    "next": ["<next-node>"]
}
```

## Node Properties

* id - Id of the node
* Abort on error - Whether to abort processing if an error occurs. Otherwise the next node is invoked.
* Invoke Next - Whether to continue processing
* Parallel - Whether to process the stream in-parallel

Read Only:
* Processed Items
* Total running time
