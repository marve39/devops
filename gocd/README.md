# Docker compose file to deploy GoCD server with x2 auto-registered GoCD agents

## Requirements
* Docker
* Docker compose

## Usage Instructions

1. Clone the repo
2. Put id_rsa and id_rsa.pub inside .ssh folder
3. copy template/cruise-config-init.xml to cruise-config.xml
4. From inside the repo run `docker-compose up -d` to run in daemon mode
5. Wait for a few minutes
6. Access the GoCD server at `http://<hostname>:8153`
7. To stop the stack use `docker-compose down`  

**Notes**

- To change the auto-reg key edit `cruise-config.xml`
- The file `cruise-config.xml` will be populated/overwritten when the stack is launched (i.e with agent reg details). For a clean re-install, edit `cruise-config.xml` and remove the `<agents>` section.

Example (remove this section):

```
  <agents>
    <agent hostname="c3ab4498e240" ipaddress="172.21.0.3" uuid="416f73c2-d33e-4cfd-a783-2ef350946b54" />
    <agent hostname="248cfcf561d6" ipaddress="172.21.0.4" uuid="822c3766-b306-42c6-bb0d-a6b8fb7f3ef7" />
  </agents>
```

- only for first installation, please run git clone inside gocd-server container to accept the host 