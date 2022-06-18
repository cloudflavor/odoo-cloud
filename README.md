Odoo in the cloud
---

This repo contains multiple ways of deploying ODOO in public as well as 
private cloud. For instructions, see the official 
[documentation](https://odoo-cloud.cloudflavor.io).

Before this is fully ready, you can check out the 
[legacy branch](https://github.com/cloudflavor/odoo-k8s/tree/legacy) that
contains instructions for an older version of ODOO.


### Building the docs

To build documentation locally, you need to install 
[mdBook](https://rust-lang.github.io/mdBook/), and then simply go to the 
[documentation dir](./documentation/) and using mdBook bin:

```shell
$  mdbook serve --open
```
