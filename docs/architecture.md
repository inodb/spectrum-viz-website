---
id: architecture
title: Architecture
sidebar_label: System Architecture
---

## Production Architecture

1. The **main webserver** is an **Nginx proxy server** on the **MSK server**. All requests are handled here and redirected to the server that runs the individual dashboard.

2. **Cassiopeia** (Landing Page) is hosted on the **MSK server**, and is the static HTML generated when building the project. The root (`/`) URL redirects to here.

3. **MSK SPECTRUM Confluence** (Wiki) is hosted on **another MSK server**, set up by MSK IT. The main webserver rewrites requests with `/wiki/` to the wiki's URL.

4. **Sylph** (Sample Processing) is hosted on the **MSK server**, self contained in a **Docker Compose** instance where only the port to its own Nginx layer is exposed. The main webserver connects to it through port 5001, and redirects requests with `/cohort/surgery/` to this port.

5. **Mira** (scRNA) is hosted on an **Azure VM**. A **Docker Compose** instance runs within it. The main webserver redirects requests with `/scrna/` to the VM's IP address.

6. **Hydra** is hosted on the **MSK server**, self contained in a **Docker Compose** instance where only the port to its own nginx layer is exposed. The main webserver connects to it through port 5005, and redirects requests with `/cohort/` to this port

## Staging Architecture

TBD
