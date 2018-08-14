### Anchore Engine How To Guide
---
Purpose:
<p> I started in the early days of docker. Back then saying we are using docker now was enough to get you past the securtiy team. But today not so much.
<p> Security teams have caught up and now so have the tools. Mature pipelines now include some sort of security scan.
<p> Looking around for a free scanner with an enterprise upgrade option is few and far between. I've seen aquasecurity but wanted to learn to use another.
<p> So below is my dive into using Anchore Engine.


###### Using Docker Compose:

<p> Using the docs with a few corrections, changes, etc...

```yaml
docker-compose up -d
```

<p> Go ahead and install the client below. Then run

```yaml
anchore-cli --u admin --p foobar --url http://localhost:8228/v1 system status
```

<p> At the time of this writing 8/13/2018. You should see something like this:

![Anchore Engine](https://github.com/roachmd/anchorenginehowto/raw/master/image/enginestatus.png)

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
anchore-cli --u admin --p foobar image vuln docker.io/library/node:latest os | wc -l
> 1669 {{ Like WTF, no really WTF NODE. }}
anchore-cli --u admin --p foobar image vuln docker.io/library/node:latest os | head
> Vulnerability ID        Package                                                Severity          Fix                    Vulnerability URL
> CVE-2015-1258           libvpx1-1.3.0-3+deb8u1                                 High              None                   https://security-tracker.debian.org/tracker/CVE-2015-1258
> CVE-2017-1000379        linux-libc-dev-3.16.57-2                               High              None                   https://security-tracker.debian.org/tracker/CVE-2017-1000379
> CVE-2017-10662          linux-libc-dev-3.16.57-2                               High              None                   https://security-tracker.debian.org/tracker/CVE-2017-10662
> CVE-2017-10663          linux-libc-dev-3.16.57-2                               High              None                   https://security-tracker.debian.org/tracker/CVE-2017-10663
```
<p> Images

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
