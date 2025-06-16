
# 1 ;理论知识 
https://stackoverflow.com/questions/69356966/what-is-image-project-argument-of-gcloud-compute-instances-create-command

[](https://stackoverflow.com/posts/69359604/timeline)

There are two types of compute engine VM images according to the [documentation](https://cloud.google.com/compute/docs/images):

> - **Public images** are provided and maintained by Google, open source communities, and third-party vendors. By default, all Google Cloud projects have access to these images and can use them to create instances.
> - **Custom images** are available only to your Cloud project. You can create a custom image from boot disks and other images. Then, use the custom image to create an instance.

Some Google managed projects with public images are: `debian-cloud`, `windows-cloud`, `centos-cloud`. In case of using public image you need to set `--image-project` value to public project id.

You can also create "Custom images" in one of your GCP projects. In this case you need to set `--image-project` value to your project id when creating inctance form custom image.

# 2 如何查找

1
使用命令  `gcloud compute image list `

```
  gcloud compute images list
NAME                                           PROJECT              FAMILY                             DEPRECATED  STATUS
centos-stream-9-v20241112                      centos-cloud         centos-stream-9                                READY
cos-105-17412-495-37                           cos-cloud            cos-105-lts                                    READY
cos-109-17800-372-38                           cos-cloud            cos-109-lts                                    READY
cos-113-18244-236-35                           cos-cloud            cos-113-lts                                    READY
cos-117-18613-75-26                            cos-cloud            cos-117-lts                                    READY
debian-11-bullseye-v20241112                   debian-cloud         debian-11                                      READY
debian-12-bookworm-arm64-v20241112             debian-cloud         debian-12-arm64                                READY
debian-12-bookworm-v20241112                   debian-cloud         debian-12                                      READY
opensuse-leap-15-5-v20240808-arm64             opensuse-cloud       opensuse-leap-arm64                            READY
opensuse-leap-15-5-v20240808-x86-64            opensuse-cloud       opensuse-leap                                  READY
opensuse-leap-15-6-v20241004-arm64             opensuse-cloud       opensuse-leap-arm64                            READY
opensuse-leap-15-6-v20241004-x86-64            opensuse-cloud       opensuse-leap                                  READY
rhel-8-v20241112                               rhel-cloud           rhel-8                                         READY
rhel-9-arm64-v20241112                         rhel-cloud           rhel-9-arm64                                   READY
rhel-9-v20241112                               rhel-cloud           rhel-9                                         READY
rhel-8-10-sap-v20241112                        rhel-sap-cloud       rhel-8-10-sap-ha                               READY
rhel-8-4-sap-v20241112                         rhel-sap-cloud       rhel-8-4-sap-ha                                READY
rhel-8-6-sap-v20241112                         rhel-sap-cloud       rhel-8-6-sap-ha                                READY
rhel-8-8-sap-v20241112                         rhel-sap-cloud       rhel-8-8-sap-ha                                READY
rhel-9-0-sap-v20241112                         rhel-sap-cloud       rhel-9-0-sap-ha                                READY
rhel-9-2-sap-v20241112                         rhel-sap-cloud       rhel-9-2-sap-ha                                READY
rhel-9-4-sap-v20241112                         rhel-sap-cloud       rhel-9-4-sap-ha                                READY
rocky-linux-8-optimized-gcp-arm64-v20241113    rocky-linux-cloud    rocky-linux-8-optimized-gcp-arm64              READY
rocky-linux-8-optimized-gcp-v20241112          rocky-linux-cloud    rocky-linux-8-optimized-gcp                    READY
rocky-linux-8-v20241112                        rocky-linux-cloud    rocky-linux-8                                  READY
rocky-linux-9-arm64-v20241112                  rocky-linux-cloud    rocky-linux-9-arm64                            READY
rocky-linux-9-optimized-gcp-arm64-v20241112    rocky-linux-cloud    rocky-linux-9-optimized-gcp-arm64              READY
rocky-linux-9-optimized-gcp-v20241112          rocky-linux-cloud    rocky-linux-9-optimized-gcp                    READY
rocky-linux-9-v20241112                        rocky-linux-cloud    rocky-linux-9                                  READY
sles-12-sp5-v20240805-x86-64                   suse-cloud           sles-12                                        READY
sles-15-sp5-v20240913-arm64                    suse-cloud           sles-15-sp5-arm64                              READY
sles-15-sp5-v20240913-x86-64                   suse-cloud           sles-15-sp5                                    READY
sles-15-sp6-v20241113-arm64                    suse-cloud           sles-15-arm64                                  READY
sles-15-sp6-v20241113-x86-64                   suse-cloud           sles-15                                        READY
sles-12-sp5-sap-v20241028-x86-64               suse-sap-cloud       sles-12-sp5-sap                                READY
sles-15-sp2-sap-v20231214-x86-64               suse-sap-cloud       sles-15-sp2-sap                                READY
sles-15-sp3-sap-v20240916-x86-64               suse-sap-cloud       sles-15-sp3-sap                                READY
sles-15-sp4-sap-v20240913-x86-64               suse-sap-cloud       sles-15-sp4-sap                                READY
sles-15-sp5-sap-v20240913-x86-64               suse-sap-cloud       sles-15-sp5-sap                                READY
sles-15-sp6-sap-v20241113-x86-64               suse-sap-cloud       sles-15-sp6-sap                                READY
sles-sap-15-sp4-hardened-v20240913-x86-64      suse-sap-cloud       sles-sap-15-sp4-hardened                       READY
sles-sap-15-sp5-hardened-v20240913-x86-64      suse-sap-cloud       sles-sap-15-sp5-hardened                       READY
sles-sap-15-sp6-hardened-v20241113-x86-64      suse-sap-cloud       sles-sap-15-sp6-hardened                       READY
ubuntu-pro-1604-xenial-v20240924               ubuntu-os-pro-cloud  ubuntu-pro-1604-lts                            READY
ubuntu-pro-1804-bionic-arm64-v20241112         ubuntu-os-pro-cloud  ubuntu-pro-1804-lts-arm64                      READY
ubuntu-pro-1804-bionic-v20241112               ubuntu-os-pro-cloud  ubuntu-pro-1804-lts                            READY
ubuntu-pro-2004-focal-arm64-v20240910          ubuntu-os-pro-cloud  ubuntu-pro-2004-lts-arm64                      READY
ubuntu-pro-2004-focal-v20240910                ubuntu-os-pro-cloud  ubuntu-pro-2004-lts                            READY
ubuntu-pro-2204-jammy-arm64-v20240927          ubuntu-os-pro-cloud  ubuntu-pro-2204-lts-arm64                      READY
ubuntu-pro-2204-jammy-v20240927                ubuntu-os-pro-cloud  ubuntu-pro-2204-lts                            READY
ubuntu-pro-2404-noble-amd64-v20241004          ubuntu-os-pro-cloud  ubuntu-pro-2404-lts-amd64                      READY
ubuntu-pro-2404-noble-arm64-v20241004          ubuntu-os-pro-cloud  ubuntu-pro-2404-lts-arm64                      READY
ubuntu-pro-fips-1804-bionic-v20241108          ubuntu-os-pro-cloud  ubuntu-pro-fips-1804-lts                       READY
cos-arm64-105-17412-495-37                     cos-cloud            cos-arm64-105-lts                              READY
cos-arm64-109-17800-372-38                     cos-cloud            cos-arm64-109-lts                              READY
cos-arm64-113-18244-236-35                     cos-cloud            cos-arm64-113-lts                              READY
cos-arm64-117-18613-75-26                      cos-cloud            cos-arm64-117-lts                              READY
cos-arm64-beta-117-18613-75-26                 cos-cloud            cos-arm64-beta                                 READY
ubuntu-2004-focal-arm64-v20241016              ubuntu-os-cloud      ubuntu-2004-lts-arm64                          READY
ubuntu-2004-focal-v20241016                    ubuntu-os-cloud      ubuntu-2004-lts                                READY
ubuntu-2204-jammy-arm64-v20240927              ubuntu-os-cloud      ubuntu-2204-lts-arm64                          READY
ubuntu-2204-jammy-v20240927                    ubuntu-os-cloud      ubuntu-2204-lts                                READY
ubuntu-pro-fips-2004-focal-v20241002           ubuntu-os-pro-cloud  ubuntu-pro-fips-2004-lts                       READY
windows-server-2016-dc-core-v20241010          windows-cloud        windows-2016-core                              READY
windows-server-2016-dc-v20241010               windows-cloud        windows-2016                                   READY
windows-server-2019-dc-core-v20241010          windows-cloud        windows-2019-core                              READY
windows-server-2019-dc-v20241010               windows-cloud        windows-2019                                   READY
windows-server-2022-dc-core-v20241010          windows-cloud        windows-2022-core                              READY
sql-2016-enterprise-windows-2016-dc-v20241010  windows-sql-cloud    sql-ent-2016-win-2016                          READY
sql-2016-enterprise-windows-2019-dc-v20241010  windows-sql-cloud    sql-ent-2016-win-2019                          READY
cos-arm64-dev-121-18747-0-0                    cos-cloud            cos-arm64-dev                                  READY
cos-arm64-stable-117-18613-75-26               cos-cloud            cos-arm64-stable                               READY
cos-beta-117-18613-75-26                       cos-cloud            cos-beta                                       READY
ubuntu-2404-noble-amd64-v20241004              ubuntu-os-cloud      ubuntu-2404-lts-amd64                          READY
ubuntu-2404-noble-arm64-v20241004              ubuntu-os-cloud      ubuntu-2404-lts-arm64                          READY
ubuntu-2410-oracular-amd64-v20241021           ubuntu-os-cloud      ubuntu-2410-amd64                              READY
ubuntu-2410-oracular-arm64-v20241021           ubuntu-os-cloud      ubuntu-2410-arm64                              READY
windows-server-2022-dc-v20241010               windows-cloud        windows-2022                                   READY
sql-2016-standard-windows-2016-dc-v20241010    windows-sql-cloud    sql-std-2016-win-2016                          READY
sql-2016-standard-windows-2019-dc-v20241010    windows-sql-cloud    sql-std-2016-win-2019                          READY
sql-2016-web-windows-2016-dc-v20241010         windows-sql-cloud    sql-web-2016-win-2016                          READY
sql-2016-web-windows-2019-dc-v20241010         windows-sql-cloud    sql-web-2016-win-2019                          READY
sql-2017-enterprise-windows-2016-dc-v20241010  windows-sql-cloud    sql-ent-2017-win-2016                          READY
cos-dev-121-18747-0-0                          cos-cloud            cos-dev                                        READY
cos-stable-117-18613-75-26                     cos-cloud            cos-stable                                     READY
ubuntu-minimal-2004-focal-arm64-v20241022      ubuntu-os-cloud      ubuntu-minimal-2004-lts-arm64                  READY
ubuntu-minimal-2004-focal-v20241022            ubuntu-os-cloud      ubuntu-minimal-2004-lts                        READY
ubuntu-minimal-2204-jammy-arm64-v20240926      ubuntu-os-cloud      ubuntu-minimal-2204-lts-arm64                  READY
ubuntu-minimal-2204-jammy-v20240926            ubuntu-os-cloud      ubuntu-minimal-2204-lts                        READY
sql-2017-enterprise-windows-2019-dc-v20241010  windows-sql-cloud    sql-ent-2017-win-2019                          READY
sql-2017-enterprise-windows-2022-dc-v20241010  windows-sql-cloud    sql-ent-2017-win-2022                          READY
sql-2017-express-windows-2016-dc-v20241010     windows-sql-cloud    sql-exp-2017-win-2016                          READY
sql-2017-express-windows-2019-dc-v20241010     windows-sql-cloud    sql-exp-2017-win-2019                          READY
sql-2017-standard-windows-2016-dc-v20241010    windows-sql-cloud    sql-std-2017-win-2016                          READY
sql-2017-standard-windows-2019-dc-v20241010    windows-sql-cloud    sql-std-2017-win-2019                          READY
sql-2017-standard-windows-2022-dc-v20241010    windows-sql-cloud    sql-std-2017-win-2022                          READY
fedora-coreos-41-20241027-3-0-gcp-aarch64      fedora-coreos-cloud  fedora-coreos-stable-arm64                     READY
fedora-coreos-41-20241027-3-0-gcp-x86-64       fedora-coreos-cloud  fedora-coreos-stable                           READY
fedora-coreos-41-20241109-1-0-gcp-aarch64      fedora-coreos-cloud  fedora-coreos-next-arm64                       READY
fedora-coreos-41-20241109-1-0-gcp-x86-64       fedora-coreos-cloud  fedora-coreos-next                             READY
fedora-coreos-41-20241109-2-0-gcp-aarch64      fedora-coreos-cloud  fedora-coreos-testing-arm64                    READY
fedora-coreos-41-20241109-2-0-gcp-x86-64       fedora-coreos-cloud  fedora-coreos-testing                          READY
ubuntu-minimal-2404-noble-amd64-v20241004      ubuntu-os-cloud      ubuntu-minimal-2404-lts-amd64                  READY
ubuntu-minimal-2404-noble-arm64-v20241004      ubuntu-os-cloud      ubuntu-minimal-2404-lts-arm64                  READY
ubuntu-minimal-2410-oracular-amd64-v20241021   ubuntu-os-cloud      ubuntu-minimal-2410-amd64                      READY
ubuntu-minimal-2410-oracular-arm64-v20241021   ubuntu-os-cloud      ubuntu-minimal-2410-arm64                      READY
sql-2017-web-windows-2016-dc-v20241010         windows-sql-cloud    sql-web-2017-win-2016                          READY
sql-2017-web-windows-2019-dc-v20241010         windows-sql-cloud    sql-web-2017-win-2019                          READY
sql-2017-web-windows-2022-dc-v20241010         windows-sql-cloud    sql-web-2017-win-2022                          READY
sql-2019-enterprise-windows-2019-dc-v20241010  windows-sql-cloud    sql-ent-2019-win-2019                          READY
sql-2019-enterprise-windows-2022-dc-v20241010  windows-sql-cloud    sql-ent-2019-win-2022                          READY
sql-2019-standard-windows-2019-dc-v20241010    windows-sql-cloud    sql-std-2019-win-2019                          READY
sql-2019-standard-windows-2022-dc-v20241010    windows-sql-cloud    sql-std-2019-win-2022                          READY
sql-2019-web-windows-2019-dc-v20241010         windows-sql-cloud    sql-web-2019-win-2019                          READY
sql-2019-web-windows-2022-dc-v20241010         windows-sql-cloud    sql-web-2019-win-2022                          READY
sql-2022-enterprise-windows-2019-dc-v20241010  windows-sql-cloud    sql-ent-2022-win-2019                          READY
sql-2022-enterprise-windows-2022-dc-v20241010  windows-sql-cloud    sql-ent-2022-win-2022                          READY
sql-2022-standard-windows-2019-dc-v20241010    windows-sql-cloud    sql-std-2022-win-2019                          READY
sql-2022-standard-windows-2022-dc-v20241010    windows-sql-cloud    sql-std-2022-win-2022                          READY
sql-2022-web-windows-2019-dc-v20241010         windows-sql-cloud    sql-web-2022-win-2019                          READY
sql-2022-web-windows-2022-dc-v20241010         windows-sql-cloud    sql-web-2022-win-2022                          READY
```

![](image/Pasted%20image%2020241113224904.png)


2

```
https://console.cloud.google.com/compute/images?project=itoperation-441318&pageState=(%22images%22:(%22s%22:%5B(%22i%22:%22family%22,%22s%22:%220%22),(%22i%22:%22type%22,%22s%22:%220%22),(%22i%22:%22name%22,%22s%22:%220%22)%5D,%22f%22:%22%255B%255D%22,%22p%22:6))
```


![](image/Pasted%20image%2020241113224840.png)
