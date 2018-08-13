### Anchore Engine How To Guide
---
Purpose:
<p> I started in the early days of docker. Back then saying we are using docker now was enough to get you past the securtiy team. But today not so much.
<p> Security teams have caught up and now so have the tools. Mature mature pipelines now include some sort of security scan.
<p> Looking around for a free scanner with an enterprise upgrade option is few and far between. I've seen aquasecurity but wanted to learn to use another.
<p> So below is my dive into using Anchore Engine.


###### Using Docker Compose:

```yaml
docker-compose up -d
```

<p> Go ahead and install the client below. Then run

```yaml
anchore-cli --u admin --p foobar --url http://localhost:8228/v1 system status
```
----
###### CLI How to
---
Installing CLI:

```bash
mkdir venv
python2.7 -m virtualenv venv
source env/bin/activate
pip install --user anchorecli
pip install anchorecli
```

Using CLI:

```yaml
anchore-cli --u admin --p foobar image add docker.io/library/node:latest
anchore-cli --u admin --p foobar image list
anchore-cli --u admin --p foobar image vuln docker.io/library/node:latest all
```
###### File Structure
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



###### Reference
https://github.com/anchore/anchore-engine
https://anchore.freshdesk.com/support/solutions/articles/36000020381-overview
