# docker-consul-backup-s3
Docker container to backup consul and upload it to s3, modified version of https://github.com/kailunshi/consul-backup

Info/Usage
-----

```
Backups consul to a s3 bucket or restore. You must provde all arguments for either backup or restore. Backup will only run if the 

Consul should be accessible on the local ipv address: curl http://169.254.169.254/latest/meta-data/local-ipv4
Consul should be accessible on the port             : 8500

Usage: consul-backup-restore  -b s3://prefix/to/path -f fileprefix
Usage: consul-backup-restore  -r s3://some/path/to/file"

-b | --s3bucket  - The s3 bucket path to use, no trailing slash
-f | --filename  - The prefix for the filename.
-r | --restore   - Use this if you want to restore, only use

restore as argument use the s3://path/to/filename url"
```

Running the container
----------------------
```
docker run blinkist/consul-backup-restore-s3 -b s3://bucket/path -f fileprefix
docker run blinkist/consul-backup-restore-s3 -r s3://bucket/path/to/file
```

To provide AWS credentials mount your .aws folder and/or set your environment
variables as needed. If you are running this inside ec2 this won't be needed
if the instance has the correct permissions to access s3.

```
docker run  -v ~/.aws:/root/.aws blinkist/consul-backup-restore-s3 -b s3://bucket/path -f fileprefix
```
