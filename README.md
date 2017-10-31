# sqs-s3-logger

A library to persist messages on S3 using serverless architecture. 
It is mainly targeted at cheaply archiving low-volume, sporadic logs from applications without a need to spin additional infrastructure.  

#### What it's not
Not a replacement for general logging systems or libraries. Provides no filtering or aggregation.

## Usage
Configure `boto3`'s credentials as per:
http://boto3.readthedocs.io/en/latest/guide/quickstart.html#configuration

Make sure you setup:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION` (optionally)

## Limitations
- Maximum SQS message size is limited to 256 KB
- There could be no more than 120,000 messages in a queue at a time.
- SQS messages cannot persist for longer than 14 days.
- Lambda environment has up to 512MB of ephemeral disk capacity.
- By default it does not guarantee correct time-based ordering

You may need to adjust your CRON settings depending on your volume.

## Testing
`python3 setup.py test`

These will use your AWS account to instantiate a temporary integration environment.  
