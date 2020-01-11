# A Hugo Static Site
Guide to deploying a Hugo built static site on Linode's Object storage.

```
git pull git@github.com:abalarin/hopeworks-demo.git
cd hopework-demo
git submodule update --init --recursive

hugo -v

s3cmd mb s3://unique-bucket-name
s3cmd ws-create --ws-index=index.html --ws-error=404.html s3://unique-bucket-name
s3cmd ws-info s3://unique-bucket-name
s3cmd --no-mime-magic --acl-public --delete-removed --delete-after sync public/ s3://unique-bucket-name
```