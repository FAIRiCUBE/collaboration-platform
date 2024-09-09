# Storage

The two types of storage "File Storage" and "Object Storage" are provided with slightly different capabilities.

## File Storage

Per default in a [FAIRiCUBE Lab JupyterLab session](jupyterlab.md) a user gets access to their personal workspace as well as a shared folder mounted under `/shared/fairicube/` or `~/.shared/fairicube/`.

The personal workspace as well as the shared folder are both persisted on File Storage.

## Object Storage

In addition an Object Storage bucket is provided separately for each Use Case for example to use with [Sentinel Hub](../external_resource/sentinelhub_access.md).

This Object Storage bucket is for convenience mounted to `~/s3` for each user but preferably used via the `s3` protocol.

On top of this bucket per Use Case there is also a shared Object Storage bucket provided accessible to all Use Cases. This is the `fairicube` bucket where access keys are shared for usage. Note that this shared bucket is not automatically mounted in the JupyterLab session.

## Sharing

Data stored on any of the Object Storage buckets can be shared via various mechanisms and services. Access to the services can be granted publicly or to authorized users only depending on the capabilities of the software tool used. An additional consideration to take into account are the costs incurred that need to be covered either by the service provider or the consumer.

The currently available services are:

* Standardized API services provided by [Sentinel Hub](../external_resource/sentinelhub_access.md)
* Direct access to the objects via S3 API
* HTTPS file access provided via [CloudFront CDN](https://aws.amazon.com/cloudfront/) which supports capabilities like custom domains, security, availability, and even adding own ones via lambda functions
* Time-limited sharing via [presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html)

Potential future services include:

* Standardized API services provided by further software supporting Object Storage like the [View Server](https://gitlab.eox.at/vs/vs) deployed in the EOxHub environment of FAIRiCUBE (needs to be evaluated on a case-by-case basis)

### Sentinel Hub

The required bucket settings to grant Sentinel Hub access are applied to all shared buckets.

After providing the data on the Object Storage bucket it needs to be registered in a [Bring Your Own COG (BYOC) collection](https://docs.sentinel-hub.com/api/latest/api/byoc/). This BYOC collection can either be used directly or in layers of map configurations.

The provider can either share the data by sharing the collection ID or by sharing the map configuration ID. The map configuration ID is typically shared as OGC service capabilities like a WMS layer.

Important to consider is who is paying for the services. The data provider always needs an SH subscription and in case of sharing the map configuration request count towards the data provider's processing units. The BYOC collection ID can only be used via an SH subscription and thus usage counts towards the processing units of the data consumer.

### S3 API

Direct access to a bucket or objects can be granted either to [individual users or publicly](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-policy-language-overview.html. An interesting configuration option in this case is the so-called [*Requester Pays* option](https://docs.aws.amazon.com/AmazonS3/latest/userguide/RequesterPaysBuckets.html). If this option is enabled the data consumer needs to use an AWS account which has to cover the incurred costs.

Public buckets should be used with caution as they easily incur considerable [costs](https://aws.amazon.com/s3/pricing/). The cost elements are data transfer (~0,09€/GB) and number of requests (~0,0004€/1.000 requests) in addition to storage costs (~0,022€/GB/month).

### CloudFront CDN

Buckets can be easily configured as origin for the [CloudFront CDN](https://aws.amazon.com/cloudfront/) which adds quite a number of standard CDN configuration capabilities to direct file access to a bucket. Also for high bandwidth buckets it should be noted that data transfer via CloudFront is generally cheaper compared to direct bucket access.

### Presigned URLs

[Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) are ideal for time-limited sharing. Note that costs are still incurred in this option.
