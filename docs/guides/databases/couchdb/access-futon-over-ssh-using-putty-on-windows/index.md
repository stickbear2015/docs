---
slug: access-futon-over-ssh-using-putty-on-windows
description: 'This tutorial will teach you how to access your CouchDB database remotely by creating an SSH tunnel with PuTTY.'
keywords: ["futon", " couchdb", " apache", " ssh", " putty", " windows", " os x", " osx"]
license: '[CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0)'
aliases: ['/databases/couchdb/securely-administer-couchdb-with-an-ssh-tunnel/','/databases/couchdb/ssh-tunnel/','/databases/couchdb/access-futon-over-ssh-using-putty-on-windows/']
modified: 2017-07-19
modified_by:
  name: Linode
published: 2010-02-04
title: Access Futon Over SSH to Administer CouchDB
external_resources:
 - '[Using PuTTY](/docs/guides/connect-to-server-over-ssh-using-putty/)'
 - '[Linode Docs - CouchDB](/docs/databases/couchdb/)'
tags: ["database"]
authors: ["Linode"]
---

[Futon](http://docs.couchdb.org/en/1.6.1/intro/futon.html) is a web-based administrative interface for [Apache CouchDB](https://couchdb.apache.org/). You can use SSH to connect to your Linode's CouchDB server and then access Futon securely through your web browser. This quick answer assumes you already have CouchDB running on your Linode.

![Access Futon Over SSH to Administer CouchDB with PuTTY](couchdb-with-futon-over-ssh-titlegraphic.png)

## Establish an SSH connection

**SSH with Windows Using PuTTY**

If you need to get set up with PuTTY, see [our guide](/docs/guides/connect-to-server-over-ssh-using-putty/) on using it and verifying your Linode's SSH key fingerprint.

To set up the SSH tunnel:

- In PuTTY's configuration window, go to the **Connection** category.
- Go to **SSH**, then **Tunnels**.
- Enter **5984** in the Source Port field and **127.0.0.1:5984** in the Destination field.
- Click **Add**, then click **Open** to log in.

![PuTTY, CouchDB, Futon](putty-couchdb-futon.png)

**SSH with Mac OS X or Linux**

Enter the following into the terminal of your local computer:

    ssh -L5984:127.0.0.1:5984 user@your_Linode's_IP


## Access Futon from a Web Browser

Once the SSH connection is established, open a web browser on your local computer and go to `http://localhost:5984/_utils/`. You'll see the Futon overview page and despite it being an http URL, you're actually connecting to your server securely through an SSH tunnel.

![Futon interface](couchdb-futon.png)

{{< note >}}
You will also be able to access CouchDB directly over its HTTP interface at `http://localhost:5984` without needing to access the server over a public IP.
{{< /note >}}
