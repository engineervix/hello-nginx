# Hello NGIИX

This directory (`hello-nginx`) contains an example of how to setup a simple site with [NGIИX](https://www.nginx.com/).

This may particularly be useful in a situation where

- you have just [setup a new Linux server](https://github.com/engineervix/ubuntu-server-setup/tree/feature/mailjet) (including installation of NGIИX) and
- you have created **A** / **CNAME** DNS records that point to your server's IP address ...

... and you want to check that your NGIИX setup is working as expected

## First things first

1. Clone this repo: `git clone https://github.com/engineervix/hello-nginx.git`
2. Create a directory for your test website. For instance, let's call it `hello_world`, and let's create it in `$HOME/PROJECTS/`. On the CLI, this would look like this:

    ```bash
    # This will also create the PROJECTS directory (if it doesn't exist) in your $HOME directory,
    # so you can change this to suit your naming & location preferences
    mkdir -p ~/PROJECTS/hello_world
    ```

3. Copy the contents of `hello-nginx` into the `hello_world` directory you created:

    ```bash
    # assuming you're in the `hello-nginx` directory
    # the -R flag is for recursively copying, the -v is for verbose mode
    cp -Rv * ~/PROJECTS/hello_world/
    ```

4. Edit the NGIИX configuration file `~/PROJECTS/hello_world/hello_world_nginx_config/example_nginx_no-https.conf` by
    - replacing `/the/path/to/your/project` with the actual **full path** to your project. This should neither be literally `$HOME/PROJECTS/hello_world` nor `~/PROJECTS/hello_world`, you have to write it in full. If your username is *kate*, for instance, then this will be `/home/kate/PROJECTS/hello_world`
    - replacing `example.org` with your actual domain

## Next Steps

1. You now need to inform NGIИX about your new site:

    ```bash
    # navigate to /etc/nginx/sites-enabled/ and in there, create a symlink to your new site's NGIИX configuration
    cd /etc/nginx/sites-enabled/
    # replace `example.org` with your own suitable reference
    sudo ln -s ~/PROJECTS/hello_world/hello_world_nginx_config/example_nginx_no-https.conf example.org
    ```

2. Test your NGIИX configuration: `sudo nginx -t`.
3. If everything is okay, reload NGIИX configuration (`sudo nginx -s reload`) and check your domain to see that you can access your simple test site.

---
