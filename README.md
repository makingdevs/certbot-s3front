## S3/CloudFront plugin for [Certbot](https://certbot.eff.org/) client

Use the certbot client to generate and install a certificate to be used with
an AWS CloudFront distribution of an S3 bucket.

### Using with Docker

Install Docker in your Local

To build a docker image of `certbot` with the `s3front` plugin, clone this repo and run:

```bash
docker build . -t certbot-s3front
```

Then export the environment variables to an `env.list` file:

```bash
echo AWS_ACCESS_KEY_ID=YOUR_ID >> env.list
echo AWS_SECRET_ACCESS_KEY=YOUR_KEY >> env.list
echo AWS_S3_BUCKET=YOUR_S3_BUCKET_NAME >> env.list
echo AWS_DISTRIBUTION_ID=YOUR_DISTRIBUTION_ID >> env.list
echo DOMAIN=YOUR_DOMAIN >> env.list
echo EMAIL=YOUR_EMAIL >> env.list
```

And finally run the docker image:

```bash
docker run --rm --name lets-encrypt -it \
    -v PATH_FOLDER/certbot-s3front/letsencrypt:/etc/letsencrypt \
    --env-file env.list \
    certbot-s3front \
```
