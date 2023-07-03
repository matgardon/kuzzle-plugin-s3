---
code: true
type: page
title: create
---

# create

Creates a S3 bucket

## Query Syntax

### HTTP

```http
URL: http://kuzzle:7512/_plugin/s3/bucket/create
Method: POST
Body:
```

```js
      {
        bucketName:"<bucketname>",
        bucketRegion:"<bucketregion>",
        bucketOptions:{ <OptionsList> },
        bucketCORS:{ <CORS> }
      }
```

### Other protocols 

```js
{
  "controller": "s3",
  "action": "create",

  "body": {
    "bucketName": "<expression>",
    "bucketRegion": "<number_of_result_max>",
    "bucketOptions": { <OptionsList> },
    "bucketCORS":{ <CORS> }
  }
}
```

## Arguments

- `bucketName`: the name of the bucket, bucket will need to follow the [AWS Bucket Name Guidelines](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html).
- `bucketRegion`: the region where you want to create the bucket, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CreateBucket.html) for available regions.
- `bucketOptions` (optional): Specify options like a custom ACL, otherwise it will default to :

```js
      {
        ACL: 'public-read'
      }
```

- `bucketCORS` (optional): Specify a custom CORS policy to add to your bucket, otherwise it will default to :

```js
      {
        AllowedHeaders: ['*'],
        AllowedMethods: ['GET', 'POST', 'PUT'],
        AllowedOrigins: ['*'],
      }
```

## Response

Returns an object with the following properties:

```js
{
  "status": 200,
  "error": null,
  "action": "create",
  "controller": "s3/bucket",
  "bucketName: "<bucketname>",
  "bucketRegion":"<bucketregion>",
  "bucketOptions": { <OptionsList> },
  "bucketCORS": { <CORS> }
}
```