# Deploying With Cyberduck
How to deploy a Static Site with Cyberduck

### Configure and Create an Object Storage Bucket with Cyberduck
1. [Download Cyberduck](https://cyberduck.io/?l=en)
2. [Install & Configue Cyberduck](https://www.linode.com/docs/platform/object-storage/how-to-use-object-storage/#install-and-configure-cyberduck)
3. [Create a bucket](https://www.linode.com/docs/platform/object-storage/how-to-use-object-storage/#create-a-bucket-with-cyberduck)

### Configure your Bucket as a Website
1. Right Click your bucket and select **Info**.

    ![select info](https://github.com/abalarin/hopeworks-demo/tree/master/readme-images/select_info.png)

2. Navigate to the **Distrubution (CDN)** tab, toggle the _Enable Website_ option and select `index.html` as the _Index File_.

    ![enable website](https://github.com/abalarin/hopeworks-demo/tree/master/readme-images/enable_website.png)

## Upload your Website to your Bucket
If you havent created your own static site your can use [this demo site](https://github.com/abalarin/hopeworks-site). If you do decide to use the demo site, **make sure** to replace all instances of `http://your-bucket.website-us-east-1.linodeobjects.com/` with the name of your bucket.

1. Select all the file in the `/public` directory of the [demo repo](https://github.com/abalarin/hopeworks-site).

    ![select files](https://github.com/abalarin/hopeworks-demo/tree/master/readme-images/select_files.png)

2. Drag them into your bucket in Cyberduck

    ![drag to bucket](https://github.com/abalarin/hopeworks-demo/tree/master/readme-images/drag_to_bucket.png)

## Visit your site! 
You can do so by navigating to the following link, but replacing it with your buckets name.

_http://your-bucket.website-us-east-1.linodeobjects.com/_