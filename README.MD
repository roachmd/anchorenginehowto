### Anchore Engine How To Guide
---


###### CLI How to
---
Installing CLI:

```
mkdir venv
python2.7 -m virtualenv venv
source env/bin/activate
pip install --user anchorecli
pip install anchorecli
```

Using CLI:

```
anchore-cli --u admin --p foobar image add docker.io/library/node:latest
anchore-cli --u admin --p foobar image list
anchore-cli --u admin --p foobar image vuln docker.io/library/node:latest all
```



##### Reference
https://github.com/anchore/anchore-engine
https://anchore.freshdesk.com/support/solutions/articles/36000020381-overview


##### File Structure
```
├── aevolume
│   ├── config
│   │   ├── analyzer_config.yaml
│   │   ├── anchore-promethesus.yaml
│   │   ├── anchore_default_bundle.json
│   │   ├── config-ui.yaml
│   │   └── config.yaml
│   └── db
├── docker-compose.yaml```
