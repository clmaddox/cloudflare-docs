---
pcx_content_type: how-to
title: Create new buckets
weight: 1
---

# Create buckets

You can create a bucket from the Cloudflare dashboard or using Wrangler.

{{<Aside type="note">}}

Wrangler is [a command-line tool](/workers/wrangler/install-and-update/) for building with Cloudflare's developer products, including R2.

The R2 support in Wrangler allows you to manage buckets and perform basic operations against objects in your buckets. For more advanced use-cases, including bulk uploads or mirroring files from legacy object storage providers, we recommend [rclone](/r2/examples/rclone/) or an [S3-compatible](/r2/api/s3/) tool of your choice.

{{</Aside>}}

## Bucket-Level Operations

Create a bucket:

```sh
$ wrangler r2 bucket create your-bucket-name
```
{{<Aside type="note">}}

Bucket names can only contain lowercase letters (a-z), numbers (0-9), and hyphens (-).

The placeholder text is only for the example.

{{</Aside>}}

List buckets in the current account:

```sh
$ wrangler r2 bucket list
```
Delete a bucket. Note that the bucket must be empty (all objects must be deleted).

```sh
$ wrangler r2 bucket delete BUCKET_TO_DELETE
```

## Notes

* Bucket names and buckets are not public by default. To allow public access to a bucket, [visit the public bucket documentation](/r2/buckets/public-buckets/).
* Invalid (unauthorized) access attempts to private buckets do not incur R2 operations charges against that bucket. Refer to the [R2 pricing FAQ](/r2/pricing/#frequently-asked-questions) to understand what operations are billed vs. not billed.
* The TLS (SSL) certificate created for each R2 bucket uses a wildcard certificate of the form `*.r2.cloudflarestorage.com`, which prevents account IDs and names from showing up in Certificate Transparency logs.
