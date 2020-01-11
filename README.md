# A Hugo Static Site
Guide to deploying a Hugo built static site on Linode's Object storage.

### Grab Source Code
```
git clone git@github.com:abalarin/hopeworks-demo.git
cd hopework-demo
git submodule update --init --recursive
```
### Create Object Storage Bucket
```
s3cmd mb s3://unique-bucket-name
```

### Edit Hugo Configuration
Set the url configuration of your Hugo site to your bucket.

`nano config.toml`
```
baseurl = "http://unique-bucket-name.website-us-east-1.linodeobjects.com/"
```

### Build the Hugo Site
This will turn all the Hugo specific files into web readable html/js/css files, and output it to the `/public` directory.
```
hugo -v
```

### Upload your Static Site to your Object Storage bucket
```
# init you bucket as a website
s3cmd ws-create --ws-index=index.html --ws-error=404.html s3://unique-bucket-name

# retrive info about your bucket
s3cmd ws-info s3://unique-bucket-name

# upload your static site to your bucket
s3cmd --no-mime-magic --acl-public --delete-removed --delete-after sync public/ s3://unique-bucket-name
```