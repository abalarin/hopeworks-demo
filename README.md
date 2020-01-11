# A Hugo Static Site
A quick guide to deploying a Hugo built static site on Linode's Object storage. For more indepth information visit Linode's guide [Host a Static Site using Linode Object Storage](https://www.linode.com/docs/platform/object-storage/host-static-site-object-storage/).

## Pre-requisites
- [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Install Hugo](https://gohugo.io/getting-started/installing/)
- [Install s3cmd](https://s3tools.org/s3cmd)
    - [Configure s3cmd for Linodes Object Storage](https://www.linode.com/docs/platform/object-storage/how-to-use-object-storage/#install-and-configure-s3cmd)

### Grab Source Code
```
# Clone this github repository
git clone git@github.com:abalarin/hopeworks-demo.git

# navigate into the newly created directory
cd hopework-demo

# fetch the requred subomdules
git submodule update --init --recursive
```
### Create Object Storage Bucket
```
# create your bucket (must be unique or you will get an error)
s3cmd mb s3://unique-bucket-name
```

### Edit Hugo Configuration
```
# open the Hugo configuration file in nano(or your editor of choice)
nano config.toml

# set the url of your Hugo site to your bucket
baseurl = "http://unique-bucket-name.website-us-east-1.linodeobjects.com/"
```

### Build the Hugo Site
This will turn all the Hugo specific files into web readable html/js/css files, and output it to the `/public` directory.
```
hugo -v
```

### Upload your Static Site to your Object Storage bucket
```
# init your bucket as a website
s3cmd ws-create --ws-index=index.html --ws-error=404.html s3://unique-bucket-name

# retrive info about your bucket (to verify you;ve vonfigured it properly)
s3cmd ws-info s3://unique-bucket-name

# upload your static site to your bucket
s3cmd --no-mime-magic --acl-public --delete-removed --delete-after sync public/ s3://unique-bucket-name
```

If you've done everything correctly you should be able to see your site at your object storage buckets endpoint: `s3cmd ws-info s3://your-bucket`