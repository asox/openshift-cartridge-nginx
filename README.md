# Openshift Nginx Cartridge
A cartridge for [Openshift](https://www.openshift.com/) that enables [Nginx](http://nginx.org/) to be used as the web server.
Based on [boekkooi/openshift-cartridge-nginx](https://github.com/boekkooi/openshift-cartridge-nginx)

## Installation
```BASH
rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/github/asox/openshift-cartridge-nginx
```

## Versions
Currently this cartridge has the following versions:
- 1.8.0

If you need another version you can compile it yourself.

### Compiling a new version
To compile a new version you will first need a openshift application.
```BASH
rhc create-app nginx http://cartreflect-claytondev.rhcloud.com/github/asox/openshift-cartridge-nginx
```

Now clone the repository and create a `nginx` folder. Now copy the `usr/compile` directory from [this](https://github.com/asox/openshift-cartridge-nginx) repository.
Now set the versions you need to compile in the `nginx/compile/versions` file. Commit and push the application repository.

SSH into you app and go to the compile folder (`cd ${OPENSHIFT_REPO_DIR}/nginx/compile`) and start compiling by running the following command:
```BASH
./all
```
Once compiling is done you can download the `nginx.tar.gz` from you application.
Extract the `nginx-{version}` from the archive and place them into the `openshift-cartridge-nginx/usr` folder.
Last but not least edit the `openshift-cartridge-nginx/manifest.yml` and add the versions.

All done just commit and push to your `openshift-cartridge-nginx` repo and use:
```BASH
http://cartreflect-claytondev.rhcloud.com/github/<user>/openshift-cartridge-nginx
```
