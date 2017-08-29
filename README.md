# go-audit-ubuntu
Playbook to deploy Go-Audit

<img src="https://alertops.com/wp-content/uploads/2016/08/slack-Logo.jpg">


```bash

apt-get install ansible
pip install ansible==VERSION

```

* Ansible Version == 2.2.1.0
* Golang Version == 1.8.3 (When available new version will be automatic upgrade)
* S.O == Ubuntu Xenial 16.04.3 LTS


# Steps before deploy:

1º Change IP address in your host file

```bash
[go-audit]
Private IP 172.33.2.7 or Public IP 216.58.211.227 Example
xxx.xxx.xxx.xxx

```

2º Change IP address in vars/main.yml

```bash
rsyslog_server: "YOUR-RSYSLOG-SERVER"
rsyslog_port: "YOUR-RSYSLOG-PORT"

```
# Deploy:

```bash
ansible-playbook  -i ansible/environments/hosts -u USER --sudo ansible/roles/go-audit/go-audit.yml  -e "host=HOST"

```

<img src="https://cdn-images-1.medium.com/max/640/1*UA09f_6GXUFMGPTARrIoOw.png">


# Testing

If everything is working well, we will see Json output logs :


```bash

systemctl status go-audit.service


Output

● go-audit.service - go-audit
   Loaded: loaded (/etc/systemd/system/go-audit.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2017-08-18 09:32:09 UTC; 1 weeks 4 days ago
 Main PID: 46335 (go-audit)
    Tasks: 13
   Memory: 6.4M
      CPU: 2min 10.525s
   CGroup: /system.slice/go-audit.service
           └─46335 /usr/bin/go-audit -config /etc/go-audit.d/go-audit.yaml

Aug 29 10:13:50 XXXXXXX go-audit[46335]: {"sequence":53373,"timestamp":"1504001630.694","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:13:53 XXXXXXX go-audit[46335]: {"sequence":53374,"timestamp":"1504001633.904","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=c654e8 a1=c60008 a2=c3f008 a3=598 items=2 p
Aug 29 10:13:54 XXXXXXX go-audit[46335]: {"sequence":53375,"timestamp":"1504001634.986","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=c5f8c8 a1=c62148 a2=c3f008 a3=598 items=2 p
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53376,"timestamp":"1504001648.605","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=c45848 a1=c675c8 a2=c3f008 a3=598 items=2 p
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53377,"timestamp":"1504001648.605","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=dd6488 a1=c675c8 a2=c3f008 a3=598 items=2 p
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53378,"timestamp":"1504001648.613","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53379,"timestamp":"1504001648.613","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53380,"timestamp":"1504001648.613","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:14:08 XXXXXXX go-audit[46335]: {"sequence":53381,"timestamp":"1504001648.617","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:14:14 XXXXXXX go-audit[46335]: {"sequence":53382,"timestamp":"1504001654.245","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=1e8b5d0 a1=7ffe17801130 a2=7ffe17801140 a3=
Aug 29 10:14:24 XXXXXXX go-audit[46335]: {"sequence":53383,"timestamp":"1504001664.776","messages":[{"type":1300,"data":"arch=c000003e syscall=59 success=yes exit=0 a0=c5d3c8 a1=c5c048 a2=c3f008 a3=598 items=2 p



```
# Licence

MIT

# Author Information

More info about official Authors go-audit --> 
https://slack.engineering/syscall-auditing-at-scale-e6a3ca8ac1b8
https://github.com/slackhq/go-audit


David Álvarez Quiroga
