# A Hugo Static Site
Guide to deploying a Hugo built static site on Linode's Object storage.

```
git pull git@github.com:abalarin/hopeworks-demo.git
git pull --recurse-submodules

hugo -v

s3cmd ws-create --ws-index=index.html --ws-error=404.html s3://demo-test

s3cmd ws-info s3://demo-site

s3cmd --no-mime-magic --acl-public --delete-removed --delete-after sync public/ s3://demo-site
```