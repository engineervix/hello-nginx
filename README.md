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
5. Test your NGIИX configuration: `sudo nginx -t`.
6. If everything is okay, restart NGIИX (`sudo systemctl restart nginx`) and check your domain to see that you can access your simple test site.

---
