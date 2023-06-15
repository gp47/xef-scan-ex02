# xef-scan-ex02

Example vulnerable helm code for xef scannig.


## Trivy manual Scanning Example

Few example results of the manual scan:
```
trivy k8s -n default --report all all   
435.53 MiB / 435.53 MiB [-----------------------------------------------------------------------------------------------------------------] 100.00% 6.08 MiB p/s 1m12s
5 / 5 [------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 0 p/s

nginx:1.14.2 (debian 9.8)

Total: 216 (UNKNOWN: 7, LOW: 43, MEDIUM: 54, HIGH: 81, CRITICAL: 31)

┌────────────────────────┬──────────────────┬──────────┬────────────────────────┬────────────────────────┬──────────────────────────────────────────────────────────────┐
│        Library         │  Vulnerability   │ Severity │   Installed Version    │     Fixed Version      │                            Title                             │
├────────────────────────┼──────────────────┼──────────┼────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ apt                    │ CVE-2020-27350   │ MEDIUM   │ 1.4.9                  │ 1.4.11                 │ apt: integer overflows and underflows while parsing .deb     │
│                        │                  │          │                        │                        │ packages                                                     │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2020-27350                   │
│                        ├──────────────────┤          │                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│                        │ CVE-2020-3810    │          │                        │ 1.4.10                 │ Missing input validation in the ar/tar implementations of    │
│                        │                  │          │                        │                        │ APT before v ......                                          │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2020-3810                    │
├────────────────────────┼──────────────────┼──────────┼────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ bsdutils               │ CVE-2016-2779    │ HIGH     │ 1:2.29.2-1+deb9u1      │                        │ util-linux: runuser tty hijack via TIOCSTI ioctl             │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2016-2779                    │
│                        ├──────────────────┼──────────┤                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│                        │ CVE-2021-37600   │ LOW      │                        │                        │ util-linux: integer overflow can lead to buffer overflow in  │
│                        │                  │          │                        │                        │ get_sem_elements() in sys-utils/ipcutils.c...                │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2021-37600                   │
├────────────────────────┼──────────────────┤          ├────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ coreutils              │ CVE-2016-2781    │          │ 8.26-3                 │                        │ coreutils: Non-privileged session can escape to the parent   │
│                        │                  │          │                        │                        │ session in chroot                                            │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2016-2781                    │
├────────────────────────┼──────────────────┼──────────┼────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ debian-archive-keyring │ DLA-2948-1       │ UNKNOWN  │ 2017.5                 │ 2017.5+deb9u2          │ debian-archive-keyring - security update                     │
├────────────────────────┼──────────────────┼──────────┼────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ dpkg                   │ CVE-2022-1664    │ CRITICAL │ 1.18.25                │ 1.18.26                │ Dpkg::Source::Archive in dpkg, the Debian package management │
│                        │                  │          │                        │                        │ system, b ...                                                │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2022-1664                    │
├────────────────────────┼──────────────────┼──────────┼────────────────────────┼────────────────────────┼──────────────────────────────────────────────────────────────┤
│ e2fslibs               │ CVE-2022-1304    │ HIGH     │ 1.43.4-2               │                        │ e2fsprogs: out-of-bounds read/write via crafted filesystem   │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2022-1304                    │
│                        ├──────────────────┼──────────┤                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│                        │ CVE-2019-5094    │ MEDIUM   │                        │ 1.43.4-2+deb9u1        │ e2fsprogs: Crafted ext4 partition leads to out-of-bounds     │
│                        │                  │          │                        │                        │ write                                                        │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2019-5094                    │
│                        ├──────────────────┤          │                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│                        │ CVE-2019-5188    │          │                        │ 1.43.4-2+deb9u2        │ e2fsprogs: Out-of-bounds write in e2fsck/rehash.c            │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2019-5188                    │
├────────────────────────┼──────────────────┼──────────┤                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│ e2fsprogs              │ CVE-2022-1304    │ HIGH     │                        │                        │ e2fsprogs: out-of-bounds read/write via crafted filesystem   │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2022-1304                    │
│                        ├──────────────────┼──────────┤                        ├────────────────────────┼──────────────────────────────────────────────────────────────┤
│                        │ CVE-2019-5094    │ MEDIUM   │                        │ 1.43.4-2+deb9u1        │ e2fsprogs: Crafted ext4 partition leads to out-of-bounds     │
│                        │                  │          │                        │                        │ write                                                        │
│                        │                  │          │                        │                        │ https://avd.aquasec.com/nvd/cve-2019-5094                    │
│                        ├──────────────────┤          │                        ├────────────────────────┼────────────────────────────────────────────────────────────
...
..
```

Deployment result example:
```
default-Deployment-v1-xef-scan-ex02-2237930648.yaml (kubernetes)

Tests: 141 (SUCCESSES: 129, FAILURES: 12, EXCEPTIONS: 0)
Failures: 12 (UNKNOWN: 0, LOW: 10, MEDIUM: 2, HIGH: 0, CRITICAL: 0)

MEDIUM: Container 'xef-scan-ex02' of Deployment 'v1-xef-scan-ex02' should set 'securityContext.allowPrivilegeEscalation' to false
══════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
A program inside the container can elevate its own privileges and run as root, which might give the program control over the container and node.

See https://avd.aquasec.com/misconfig/ksv001
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 default-Deployment-v1-xef-scan-ex02-2237930648.yaml:133-142
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 133 ┌                 - image: nginx:1.14.2
 134 │                   imagePullPolicy: IfNotPresent
 135 │                   name: xef-scan-ex02
 136 │                   ports:
 137 │                     - containerPort: 80
 138 │                       name: http
 139 │                       protocol: TCP
 140 │                   resources: {}
 141 │                   terminationMessagePath: /dev/termination-log
 142 └                   terminationMessagePolicy: File
```

You can also scan specific workloads that are running in your cluster, such as our deployment:
```
trivy k8s -n default --report summary deployment/v1-xef-scan-ex02

Workload Assessment
┌───────────┬─────────────────────────────┬───────────────────────┬────────────────────┬───────────────────┐
│ Namespace │          Resource           │    Vulnerabilities    │ Misconfigurations  │      Secrets      │
│           │                             ├────┬────┬────┬────┬───┼───┬───┬───┬────┬───┼───┬───┬───┬───┬───┤
│           │                             │ C  │ H  │ M  │ L  │ U │ C │ H │ M │ L  │ U │ C │ H │ M │ L │ U │
├───────────┼─────────────────────────────┼────┼────┼────┼────┼───┼───┼───┼───┼────┼───┼───┼───┼───┼───┼───┤
│ default   │ Deployment/v1-xef-scan-ex02 │ 31 │ 81 │ 54 │ 43 │ 7 │   │   │ 2 │ 10 │   │   │   │   │   │   │
└───────────┴─────────────────────────────┴────┴────┴────┴────┴───┴───┴───┴───┴────┴───┴───┴───┴───┴───┴───┘
Severities: C=CRITICAL H=HIGH M=MEDIUM L=LOW U=UNKNOWN
```
or
```
trivy k8s -n default --severity CRITICAL --report summary all
5 / 5 [------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 3 p/s

Summary Report for rancher-desktop


Workload Assessment
┌───────────┬─────────────────────────────┬─────────────────┬───────────────────┬─────────┐
│ Namespace │          Resource           │ Vulnerabilities │ Misconfigurations │ Secrets │
│           │                             ├─────────────────┼───────────────────┼─────────┤
│           │                             │        C        │         C         │    C    │
├───────────┼─────────────────────────────┼─────────────────┼───────────────────┼─────────┤
│ default   │ Deployment/v1-xef-scan-ex02 │       31        │                   │         │
└───────────┴─────────────────────────────┴─────────────────┴───────────────────┴─────────┘
Severities: C=CRITICAL
```