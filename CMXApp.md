- [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)
  - [Test Summary](#test-summary)
  - [Prerequisites](#prerequisites)
  - [Hardware Requirements](#hardware-requirements)
  - [Test steps](#test-steps)
  
- [ITP/RI/ICMAH/02: Verify ONF portal access for sdran contents with invalid credentials](#itpriicmah02-Verify-ONF-portal-access-for-sdran-contents-with-invalid-credentials)
  - [Test Summary](#test-summary-1)
  - [Prerequisites](#prerequisites-1)
  - [Test steps](#test-steps-1)

- [ITP/RI/ICMAH/03: Verify recovery of single node cluster with Intelligent Connection Management RI from forced reboot](#itpriicmah03-Verify-recovery-of-single-node-cluster-with-Intelligent-Connection-Management-RI-from-forced-reboot)
  - [Test Summary](#test-summary-2)
  - [Prerequisites](#prerequisites-2)
  - [Test steps](#test-steps-2)

- [ITP/RI/ICMAH/04: Verify uninstall and install of Intelligent Connection Management for Automated Handover RI](#itpriicmah04-Verify-uninstall-and-install-of-Intelligent-Connection-Management-for-Automated-Handover-RI)
  - [Test Summary](#test-summary-3)
  - [Prerequisites](#prerequisites-3)
  - [Test steps](#test-steps-3)

- [ITP/RI/ICMAH/05: Delete Intelligent Connection Management application pod and verify its recovery and functionality](#itpriicmah05-Delete-Intelligent-Connection-Management-application-pod-and-verify-its-recovery-and-functionality)
  - [Test Summary](#test-summary-4)
  - [Prerequisites](#prerequisites-4)
  - [Test steps](#test-steps-4)

- [ITP/RI/ICMAH/06: Verify Product key integrity during ICMAH installation](#itpriicmah06-Verify-Product-key-integrity-during-ICMAH-installation)
  - [Test Summary](#test-summary-5)
  - [Prerequisites](#prerequisites-5)
  - [Test steps](#test-steps-5)
  
- [ITP/RI/ICMAH/07: Verify reinstallation of Intelligent Connection Management for Automated Handover RI](#itpriicmah07-Verify-reinstallation-of-Intelligent-Connection-Management-for-Automated-Handover-RI)
  - [Test Summary](#test-summary-6)
  - [Prerequisites](#prerequisites-6)
  - [Test steps](#test-steps-6)

- [ITP/RI/ICMAH/08: Verify ICMAH RI installation with product key of another RI instance](#itpriicmah08-Verify-ICMAH-RI-installation-with-product-key-of-another-RI-instance)
  - [Test Summary](#test-summary-7)
  - [Prerequisites](#prerequisites-7)
  - [Test steps](#test-steps-7)

- [ITP/RI/ICMAH/09: Verify uninstall and install of ICMAH RI with an invalid product key](#itpriicmah09-Verify-uninstall-and-install-of-ICMAH-RI-with-an-invalid-product-key)
  - [Test Summary](#test-summary-8)
  - [Prerequisites](#prerequisites-8)
  - [Test steps](#test-steps-8)

- [ITP/RI/ICMAH/10: Verify uninstall of ICMAH RI followed by an abort signal for previous cleanup instance](#itpriicmah10-Verify-uninstall-of-ICMAH-RI-followed-by-an-abort-signal-for-previous-cleanup-instance)
  - [Test Summary](#test-summary-9)
  - [Prerequisites](#prerequisites-9)
  - [Test steps](#test-steps-9)
  
- [ITP/RI/ICMAH/11: Verify ICMAH RI installation with an invalid credentials for ONF portal after successful install and uninstall cycle](#itpriicmah11-Verify-ICMAH-RI-installation-with-an-invalid-credentials-for-ONF-portal-after-successful-install-and-uninstall-cycle)
  - [Test Summary](#test-summary-10)
  - [Prerequisites](#prerequisites-10)
  - [Test steps](#test-steps-10)
  
- [ITP/RI/ICMAH/12: Verify E2E Latency measurement of CMxApp meets the ORAN KPI using OPENVINO](#itpriicmah12-Verify-E2E-Latency-measurement-of-CMxApp-meets-the-ORAN-KPI-using-OPENVINO)
  - [Test Summary](#test-summary-11)
  - [Prerequisites](#prerequisites-11)
  - [Test steps](#test-steps-11)

- [ITP/RI/ICMAH/13: Verify E2E Latency measurement of CMxApp meets the ORAN KPI using Python](#itpriicmah13-Verify-E2E-Latency-measurement-of-CMxApp-meets-the-ORAN-KPI-using-Python)
  - [Test Summary](#test-summary-12)
  - [Prerequisites](#prerequisites-12)
  - [Test steps](#test-steps-12)
 
## ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification

### Test Summary

Intelligent Connection Management xApp is developed based on the O-RAN network architecture to optimize user association and load balancing to improve the quality of service (QoS) requirements of a user equipment (UE). The connection management is formulated as a combinatorial graph optimization problem. A deep reinforcement learning (DRL) solution is proposed to learn the weights of a graph neural network (GNN) for an optimal UE association.<br>
The Intel® Smart Edge Open Developer Experience Kit platform infrastructure is used to deploy the SD-RAN 1.3 release version of RIC pod, RAN Simulator pod, and Intelligent Connection Management xApp pod. The CM xApp interacts with the RIC to fetch network data from RAN simulator and performs handover of UEs across different cells.



### Prerequisites

- <a href="https://wiki.ith.intel.com/display/ESSE/Enable+Intel+SGX+in+BIOS">Enable SGX in BIOS</a>

- Configure DCAP service (once, if not available):
  - Subscribe to the Intel PCS 
  
    (https://www.intel.com/content/www/us/en/developer/articles/guide/intel-software-guard-extensions-data-center-attestation-primitives-quick-install-guide.html#inpage-nav-2-undefined)

  - Set up the Intel PCCS 
  
    (https://www.intel.com/content/www/us/en/developer/articles/guide/intel-software-guard-extensions-data-center-attestation-primitives-quick-install-guide.html#inpage-nav-2-1)
  
-  <a href="https://wiki.ith.intel.com/display/ESSE/CM+xApp+on+SE-O+DEK+21.12#CMxApponSEODEK21.12-StepstoStandaloneVMInstanceanddeployDEK">Install Verification Controller</a>
    
- Intel® Smart Edge Open Developer Experience Kit deployed in target platform - https://github.com/intel-innersource/applications.services.smart-edge-open.docs/blob/main/experience-kits/developer-experience-kit.md
- ONF credentials in order to get access to the SD-RAN release
      https://opennetworking.org/join-onf/ gives the membership details
      https://opennetworking.org/contact/ Fill in the form for membership query.<br> Once a company is a member of ONF, all employees of that company have access to all membership privileges.
- Recommended to use docker pro account mapped to private docker images hosted for this installation.
   
- BIOS version on target system must be 1.3.8 or high. To upgrade the BIOS link please follow the below link.
  
  https://wiki.ith.intel.com/display/ESSE/Updating+DELL+PowerEdge+R750+BIOS
 
- refer following link for ESP-ISO ESP w/ Ubuntu OS image creation
-(https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/blob/main/test_plans/se-o/esp/singlenode/ts01-esp-platform-setup-singlenode.md#itpseoespsingle0102-deploy-esp-on-host-machine-with-ubuntu-provision-target-machine-with-ubuntu-profile-using-usb-boot-method)

### Hardware Requirements

Intel® Smart Edge Open Node

- Intel® Xeon® scalable processor
- At least 64 GB RAM
- At least 265 GB hard drive
- An Internet connection
- Ubuntu* 20.04 LTS

### Test Steps

**Step 1 : Install the Reference Implementation**

1. Download the Reference Implementation ESH package from the following link with required specifications:
   https://recipeconfigurator-quiet-toucan.apps1-bg-int.icloud.intel.com/iot/edgesoftwarehub/download/home/ri/Intelligent_Connection_Management

    Select and download required version to be tested as shown below:
   ![image](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/a774d64f-89dd-4e9e-818c-7cdd7ea87aa7)

    
2. Once your download is complete, open a new terminal as a non root user ex: "smartedge-open" and copy the zip package to the target system /home/smartedge-open folder.

    ```shell
    $ mv <path-of-downloaded-directory>/Intelligent_Connection_Management.zip /home/smartedge-open/
    ```

3. Unzip the RI package and change permission of 'edgesoftware' executable file

    ```shell
    $ cd /home/smartedge-open
    $ unzip Intelligent_Connection_Management_for_Automated_Handover.zip 
    $ cd Intelligent_Connection_Management
    $ chmod 755 edgesoftware 
    ```

4. Run the command below to install the Reference Implementation:

    ```shell
    $ ./edgesoftware install
    ```

5. During the installation, user shall be prompted for the Product Key. The Product Key is contained in the email you received from Intel confirming your download.
 
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware install
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  <Product-Key>
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    Successfully validated Product Key
    Checking for prerequisites
    ```

    ```shell
    --------Succesfuly installed prerequisites--------
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 1.2%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    100%|██████████████████████████████████████████████████████████████████████████████████████████████████████| 44.0M/44.0M [00:43<00:00, 1.01MiB/s]
    Module validation passed for 6022bd8ccc7449002afdbedd
    Successfully downloaded module esb_common
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    100%|███████████████████████████████████████████████████████████████████████████████████████████████████████| 1.95M/1.95M [00:02<00:00, 951kiB/s]
    Module validation passed for 619b8bceff6f230021e4409e
    Successfully downloaded module Intelligent_Connection_Management_for_Automated_Handover
    Downloading modules completed...
    Installing shared module 'esb_common'
    Unzipping the shared module 'esb_common'...
    running install
    running bdist_egg
    running egg_info
    creating esb_common.egg-info
    writing esb_common.egg-info/PKG-INFO
    writing dependency_links to esb_common.egg-info/dependency_links.txt
    writing top-level names to esb_common.egg-info/top_level.txt
    writing manifest file 'esb_common.egg-info/SOURCES.txt'
    reading manifest file 'esb_common.egg-info/SOURCES.txt'
    writing manifest file 'esb_common.egg-info/SOURCES.txt'
    installing library code to build/bdist.linux-x86_64/egg
    ```

    ```shell
    creating build
    creating build/bdist.linux-x86_64
    creating build/bdist.linux-x86_64/egg
    creating build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/PKG-INFO -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/SOURCES.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/dependency_links.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/top_level.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    zip_safe flag not set; analyzing archive contents...
    creating dist
    creating 'dist/esb_common-0.1-py3.8.egg' and adding 'build/bdist.linux-x86_64/egg' to it
    removing 'build/bdist.linux-x86_64/egg' (and everything under it)
    Processing esb_common-0.1-py3.8.egg
    Copying esb_common-0.1-py3.8.egg to /usr/local/lib/python3.8/dist-packages
    Adding esb-common 0.1 to easy-install.pth file

    Installed /usr/local/lib/python3.8/dist-packages/esb_common-0.1-py3.8.egg
    Processing dependencies for esb-common==0.1
    Finished processing dependencies for esb-common==0.1
    Successfully installed shared module 'esb_common'.
    Installing Lanternrock SDK
    Successfully installed Lanternrock SDK.
    Unzipping the module Intelligent_Connection_Management_for_Automated_Handover...
    Modules to be installed by package are ['Intelligent_Connection_Management_for_Automated_Handover']
    Installing Intelligent_Connection_Management_for_Automated_Handover
    Verifying SE Node (xx.xxx.xxx.xxx)                  [..................................................] 100%


    Before installing freshly, deleting partially installed pods if any ...
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp quietly                        [..................................................] 100%
    ```

6. During the installation, user shall be prompted to enter username and password for ONF portal to download SDRAN helm chart.

    ```shell
    Please contact ONF(https://opennetworking.org/contact/) for username and password credentials that allow access to the sdran helm chart repo.
    Enter sdran username: intel
    Enter sdran password: <ONF Password>
    Installing CM Xapp dependencies on SE Node . . .   [..................................................] 100%
    Successfully installed: SDRAN
    ```
  
8. When the installation is complete, you shall see the message **Installation of package complete** with the installation status for each module.

    ```shell
    CM Xapp installation started. This might take upto 1 mins
    Installing CM Xapp                                 [..................................................] 100%
    Successfully installed: CM Xapp

    Verifying CM Xapp installation in (xx.xxx.xxx.xxx)  [..................................................] 100%
    Successfully installed Intelligent_Connection_Management_for_Automated_Handover took 13 minutes 58.31 seconds
    Installation of package complete
    ***Recommended to reboot system after installation***
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```
    **Note:** Installation logs are available at path: /var/log/esb-cli/Intelligent_Connection_Management_for_Automated_Handover_1.0.0/Intelligent_Connection_Management_for_Automated_Handover/install.log

9. If Intel® Smart Edge Open Developer Experience Kit is installed successfully along with the RI, running the following command should show output similar to the example below. All the pods should be either in the 'Running' or 'Completed' stage. 
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -A
    NAMESPACE                NAME                                                         READY   STATUS    RESTARTS   AGE
    harbor                   harbor-app-chartmuseum-7cb556754f-hb44g                      1/1     Running   0          22h
    harbor                   harbor-app-core-7486954668-qc2k9                             1/1     Running   0          22h
    harbor                   harbor-app-database-0                                        1/1     Running   0          22h
    harbor                   harbor-app-jobservice-5857d646f-sq2cd                        1/1     Running   0          22h
    harbor                   harbor-app-nginx-65dd6bc7b7-blvp4                            1/1     Running   0          22h
    harbor                   harbor-app-notary-server-5799b54bf6-7v2f2                    1/1     Running   0          22h
    harbor                   harbor-app-notary-signer-5f8d5dfcc9-2dsgc                    1/1     Running   0          22h
    harbor                   harbor-app-portal-88895f59f-5fwp9                            1/1     Running   0          22h
    harbor                   harbor-app-redis-0                                           1/1     Running   0          22h
    harbor                   harbor-app-registry-76546fc777-5n25s                         2/2     Running   0          22h
    harbor                   harbor-app-trivy-0                                           1/1     Running   0          22h
    kube-system              atomix-controller-6767f468cc-n274n                           1/1     Running   0          18m
    kube-system              atomix-raft-storage-controller-85db5888f6-hwd8b              1/1     Running   0          18m
    kube-system              calico-kube-controllers-6b59cd85f8-9klzg                     1/1     Running   0          22h
    kube-system              calico-node-tvcx5                                            1/1     Running   0          22h
    kube-system              coredns-558bd4d5db-nfx4f                                     1/1     Running   0          22h
    kube-system              coredns-558bd4d5db-xhtzx                                     1/1     Running   0          22h
    kube-system              etcd-ubuntu-4b70b7ba43                                       1/1     Running   0          22h
    kube-system              kube-apiserver-ubuntu-4b70b7ba43                             1/1     Running   0          22h
    kube-system              kube-controller-manager-ubuntu-4b70b7ba43                    1/1     Running   0          22h
    kube-system              kube-multus-ds-amd64-xgk2l                                   1/1     Running   0          21h
    kube-system              kube-proxy-nv4cb                                             1/1     Running   0          22h
    kube-system              kube-scheduler-ubuntu-4b70b7ba43                             1/1     Running   0          22h
    kube-system              onos-operator-app-6864f6f77c-95sz2                           1/1     Running   0          17m
    kube-system              onos-operator-config-7569c46b76-qlj24                        1/1     Running   0          17m
    kube-system              onos-operator-topo-7c68bc4d7-lqkh4                           1/1     Running   0          17m
    smartedge-apps           cm-xapp-6d99d58b5-f8lgg                                      1/1     Running   0          6m46s
    smartedge-apps           onos-cli-764d9697fb-t2gnj                                    1/1     Running   0          17m
    smartedge-apps           onos-consensus-store-0                                       1/1     Running   0          17m
    smartedge-apps           onos-e2t-797bf77554-rjlrr                                    3/3     Running   0          17m
    smartedge-apps           onos-topo-79f7c5c54d-tgtgj                                   3/3     Running   0          17m
    smartedge-apps           onos-uenib-6f7466c87f-v5jmr                                  3/3     Running   0          17m
    smartedge-apps           ran-simulator-55dc5f56c6-94ltx                               1/1     Running   0          16m
    smartedge-system         nfd-release-node-feature-discovery-master-6c8ff5486d-xs8x2   1/1     Running   0          21h
    smartedge-system         nfd-release-node-feature-discovery-worker-kh7lh              1/1     Running   0          21h
    sriov-network-operator   network-resources-injector-zv6j2                             1/1     Running   0          21h
    sriov-network-operator   operator-webhook-qzv7x                                       1/1     Running   0          21h
    sriov-network-operator   sriov-device-plugin-cwfhq                                    1/1     Running   0          21h
    sriov-network-operator   sriov-network-config-daemon-f28l9                            3/3     Running   0          21h
    sriov-network-operator   sriov-network-operator-68598c6fc6-ttn79                      1/1     Running   0          21h
    telemetry                cadvisor-mknz2                                               2/2     Running   0          21h
    telemetry                collectd-ss2j8                                               3/3     Running   0          21h
    telemetry                grafana-6867674556-cqp8c                                     3/3     Running   0          21h
    telemetry                prometheus-node-exporter-mcwj6                               1/1     Running   0          21h
    telemetry                prometheus-server-5b469cc688-swgx2                           3/3     Running   0          21h
    telemetry                statsd-exporter-cfbd5bf65-jcgc8                              2/2     Running   0          21h
    ```
  
**Step 2 : Verify the SD-RAN ran simulator pods for UEs & Cells**

1. Run "kubectl get pods -n smartedge-apps" to get the <onos cli> pod name.
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps | grep onos-cli
    onos-cli-764d9697fb-t2gnj        1/1     Running   0          57m
    ```
  
2. Verify the UE count with command below, output should show '100'

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-t2gnj -- onos ransim get ueCount
    100
    ```
  
3. Run the command below to see all the 100 UEs with their RRC states
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-t2gnj -- onos ransim
    get ues
    IMSI             Serving Cell     CRNTI      Admitted   RRC
    5251154          13842601454c005  90224      false      RRCSTATUS_CONNECTED
    1711504          13842601454c001  90128      false      RRCSTATUS_IDLE
    6141541          13842601454c005  90147      false      RRCSTATUS_IDLE
    8642060          13842601454c004  90174      false      RRCSTATUS_CONNECTED
    7397573          13842601454c001  90180      false      RRCSTATUS_IDLE
    4725213          13842601454c004  90187      false      RRCSTATUS_CONNECTED
    9533192          13842601454c005  90135      false      RRCSTATUS_CONNECTED
    3058868          13842601454c002  90138      false      RRCSTATUS_IDLE
    1116521          13842601454c003  90205      false      RRCSTATUS_IDLE
    6737672          13842601454c002  90223      false      RRCSTATUS_CONNECTED
    7038074          13842601454c005  90146      false      RRCSTATUS_IDLE
    3148025          13842601454c005  90149      false      RRCSTATUS_IDLE
    7074160          13842601454c005  90158      false      RRCSTATUS_IDLE
    4600052          13842601454c004  90166      false      RRCSTATUS_CONNECTED
    2542837          13842601454c004  90212      false      RRCSTATUS_CONNECTED
    8710157          13842601454c001  90220      false      RRCSTATUS_IDLE
    9884595          13842601454c005  90165      false      RRCSTATUS_CONNECTED
    8395224          13842601454c005  90197      false      RRCSTATUS_IDLE
    7143387          13842601454c001  90202      false      RRCSTATUS_IDLE
    1497971          13842601454c004  90203      false      RRCSTATUS_IDLE
    4040402          13842601454c003  90216      false      RRCSTATUS_IDLE
    4530788          13842601454c005  90129      false      RRCSTATUS_CONNECTED
    2570923          13842601454c001  90172      false      RRCSTATUS_IDLE
    2594692          13842601454c003  90199      false      RRCSTATUS_IDLE
    4831708          13842601454c002  90210      false      RRCSTATUS_CONNECTED
    5902719          13842601454c005  90215      false      RRCSTATUS_CONNECTED
    6661511          13842601454c001  90157      false      RRCSTATUS_CONNECTED
    1373821          13842601454c002  90162      false      RRCSTATUS_CONNECTED
    4547819          13842601454c005  90185      false      RRCSTATUS_CONNECTED
    1483304          13842601454c002  90189      false      RRCSTATUS_CONNECTED
    1435183          13842601454c005  90190      false      RRCSTATUS_CONNECTED
    7018203          13842601454c004  90221      false      RRCSTATUS_IDLE
    2756326          13842601454c002  90206      false      RRCSTATUS_IDLE
    8580427          13842601454c002  90142      false      RRCSTATUS_CONNECTED
    5156858          13842601454c002  90150      false      RRCSTATUS_CONNECTED
    1672631          13842601454c003  90168      false      RRCSTATUS_IDLE
    4391794          13842601454c005  90200      false      RRCSTATUS_CONNECTED
    2988809          13842601454c003  90204      false      RRCSTATUS_CONNECTED
    2115827          13842601454c005  90193      false      RRCSTATUS_CONNECTED
    4772388          13842601454c001  90194      false      RRCSTATUS_CONNECTED
    6686199          13842601454c004  90207      false      RRCSTATUS_CONNECTED
    2995449          13842601454c005  90136      false      RRCSTATUS_CONNECTED
    4818079          13842601454c005  90144      false      RRCSTATUS_CONNECTED
    9526719          13842601454c002  90151      false      RRCSTATUS_CONNECTED
    1666565          13842601454c001  90153      false      RRCSTATUS_CONNECTED
    3864494          13842601454c005  90159      false      RRCSTATUS_IDLE
    5474933          13842601454c005  90218      false      RRCSTATUS_IDLE
    3915551          13842601454c001  90191      false      RRCSTATUS_CONNECTED
    2646713          13842601454c001  90195      false      RRCSTATUS_IDLE
    7846364          13842601454c003  90127      false      RRCSTATUS_IDLE
    3745281          13842601454c001  90155      false      RRCSTATUS_CONNECTED
    7649166          13842601454c003  90173      false      RRCSTATUS_CONNECTED
    3395389          13842601454c004  90176      false      RRCSTATUS_CONNECTED
    9205120          13842601454c003  90222      false      RRCSTATUS_IDLE
    6800136          13842601454c005  90192      false      RRCSTATUS_CONNECTED
    9549401          13842601454c002  90211      false      RRCSTATUS_CONNECTED
    2074472          13842601454c004  90213      false      RRCSTATUS_IDLE
    2152316          13842601454c005  90125      false      RRCSTATUS_CONNECTED
    7695435          13842601454c004  90148      false      RRCSTATUS_CONNECTED
    6183562          13842601454c002  90164      false      RRCSTATUS_CONNECTED
    3229991          13842601454c005  90175      false      RRCSTATUS_IDLE
    8146853          13842601454c001  90177      false      RRCSTATUS_IDLE
    5400103          13842601454c005  90178      false      RRCSTATUS_CONNECTED
    2727090          13842601454c004  90182      false      RRCSTATUS_CONNECTED
    9480303          13842601454c005  90214      false      RRCSTATUS_IDLE
    6831584          13842601454c005  90134      false      RRCSTATUS_CONNECTED
    1808263          13842601454c003  90137      false      RRCSTATUS_IDLE
    5494183          13842601454c005  90141      false      RRCSTATUS_IDLE
    8262401          13842601454c005  90167      false      RRCSTATUS_IDLE
    5929921          13842601454c002  90169      false      RRCSTATUS_CONNECTED
    7775118          13842601454c005  90181      false      RRCSTATUS_IDLE
    8698055          13842601454c003  90208      false      RRCSTATUS_CONNECTED
    3583449          13842601454c004  90132      false      RRCSTATUS_IDLE
    8497897          13842601454c001  90139      false      RRCSTATUS_IDLE
    5701947          13842601454c001  90152      false      RRCSTATUS_IDLE
    2762890          13842601454c004  90156      false      RRCSTATUS_CONNECTED
    3340531          13842601454c002  90161      false      RRCSTATUS_IDLE
    3398530          13842601454c003  90163      false      RRCSTATUS_CONNECTED
    2576944          13842601454c005  90170      false      RRCSTATUS_CONNECTED
    9189062          13842601454c005  90171      false      RRCSTATUS_CONNECTED
    4819419          13842601454c004  90126      false      RRCSTATUS_CONNECTED
    4411495          13842601454c003  90130      false      RRCSTATUS_CONNECTED
    1504142          13842601454c004  90140      false      RRCSTATUS_CONNECTED
    3086686          13842601454c002  90154      false      RRCSTATUS_IDLE
    9492561          13842601454c005  90160      false      RRCSTATUS_IDLE
    9722999          13842601454c005  90183      false      RRCSTATUS_CONNECTED
    1359777          13842601454c004  90184      false      RRCSTATUS_IDLE
    8982789          13842601454c005  90196      false      RRCSTATUS_IDLE
    2091492          13842601454c005  90179      false      RRCSTATUS_IDLE
    4540702          13842601454c002  90186      false      RRCSTATUS_IDLE
    9677910          13842601454c005  90188      false      RRCSTATUS_CONNECTED
    4600225          13842601454c004  90198      false      RRCSTATUS_CONNECTED
    3613098          13842601454c005  90209      false      RRCSTATUS_IDLE
    2714040          13842601454c003  90217      false      RRCSTATUS_CONNECTED
    9855651          13842601454c004  90219      false      RRCSTATUS_IDLE
    1833557          13842601454c005  90131      false      RRCSTATUS_IDLE
    7303136          13842601454c004  90133      false      RRCSTATUS_IDLE
    8541660          13842601454c002  90143      false      RRCSTATUS_IDLE
    1299704          13842601454c004  90145      false      RRCSTATUS_IDLE
    3147694          13842601454c003  90201      false      RRCSTATUS_CONNECTED
    ```
  
4. Run the command below to verify the 5 Cells with TxDB, Neighbors details 
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-t2gnj -- onos ransim get cells
    NCGI                 #UEs Max UEs    TxDB       Lat       Lng Azimuth     Arc   A3Offset     TTT  A3Hyst PCellOffset FreqOffset      PCI    Color Idle Conn Neighbors(NCellOffset)
    13842601454c002         0      20   40.00    12.969    77.753       0     120          0       0       0          0          0      119    green    9,    6, 13842601454c001(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c005         0      20   40.00    12.970    77.749     120     120          0       0       0          0          0      122    green   16,   20, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c004(0)
    13842601454c001         0      20   40.00    12.969    77.749       0     120          0       0       0          0          0      118    green    9,    9, 13842601454c002(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c003         0      20   40.00    12.970    77.754       0     120          0       0       0          0          0      120    green    6,    4, 13842601454c001(0),13842601454c002(0),13842601454c004(0),13842601454c005(0)
    13842601454c004         0      20   40.00    12.971    77.751       0     120          0       0       0          0          0      121    green    7,   14, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c005(0)
    ```
  
5. Verify the subscription details with command below
 
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-t2gnj -- onos e2t list subscriptions
    Subscription ID                              Revision   Service Model ID   E2 NodeID   Encoding   Phase               State
    14d96d88f13bba8ba7889bdf532c059d:e2:1/5153   207        oran-e2sm-mho:v1   e2:1/5153   ASN1_PER   SUBSCRIPTION_OPEN   SUBSCRIPTION_COMPLETE
    bab81642e0e6d82c57a54060feeabe6f:e2:1/5153   214        oran-e2sm-mho:v1   e2:1/5153   ASN1_PER   SUBSCRIPTION_OPEN   SUBSCRIPTION_COMPLETE
    76d79858affefc5ecef79683581f1561:e2:1/5153   217        oran-e2sm-mho:v1   e2:1/5153   ASN1_PER   SUBSCRIPTION_OPEN   SUBSCRIPTION_COMPLETE
    ```

6. To check the subscription requests to the e2 node, run the following command on the app logs.
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps | grep cm
    cm-xapp-6d99d58b5-f8lgg          1/1     Running   0          92m
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl logs -n smartedge-apps cm-xapp-6d99d58b5-f8lgg | grep "Create subscription successful"
    2021-12-12T15:52:12.685Z        INFO    xapp/client     pkg/client.go:272       Create subscription successful for nodeID %!(EXTRA topo.ID=e2:1/5153, string= with subscription name , string=onos-cm-xapp-subscription-MHO_TRIGGER_TYPE_PERIODIC)
    2021-12-12T15:52:12.763Z        INFO    xapp/client     pkg/client.go:272       Create subscription successful for nodeID %!(EXTRA topo.ID=e2:1/5153, string= with subscription name , string=onos-cm-xapp-subscription-MHO_TRIGGER_TYPE_UPON_RCV_MEAS_REPORT)
    2021-12-12T15:52:12.773Z        INFO    xapp/client     pkg/client.go:272       Create subscription successful for nodeID %!(EXTRA topo.ID=e2:1/5153, string= with subscription name , string=onos-cm-xapp-subscription-MHO_TRIGGER_TYPE_UPON_CHANGE_RRC_STATUS)  
    ```
  
7. Verify the CM xApp logs to confirm that the App is issuing the handover requests.<br>This command needs to be run after 5 mins of starting the Application. 

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl logs -n smartedge-apps cm-xapp-6d99d58b5-f8lgg | grep "Calling cont
    rol req"
    12/12/2021 03:54:14 PM Calling control req no 1 for UE : 3340531 Serving cell: 13842601454c004 target_cell 13842601454c002
    12/12/2021 03:54:25 PM Calling control req no 2 for UE : 3340531 Serving cell: 13842601454c002 target_cell 13842601454c001
    12/12/2021 03:54:53 PM Calling control req no 3 for UE : 1711504 Serving cell: 13842601454c001 target_cell 13842601454c003
    12/12/2021 03:55:04 PM Calling control req no 4 for UE : 8698055 Serving cell: 13842601454c002 target_cell 13842601454c003
    12/12/2021 03:55:10 PM Calling control req no 5 for UE : 7143387 Serving cell: 13842601454c004 target_cell 13842601454c003
    ...
    ```
  
8. Verify the RAN Sim logs to confirm whether the handover requests issued from xApp are reaching the Ran Simulator.<br>This command needs to be run after 5 mins of starting the Application
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps | grep ran
    ran-simulator-55dc5f56c6-94ltx   1/1     Running   0          117m
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl logs -n smartedge-apps ran-simulator-55dc5f56c6-94ltx | grep "HO is done successfully"
    2021-12-12T15:42:13.085Z        INFO    mobility/driver mobility/driver.go:344  HO is done successfully: 2756326 to &{87893173159116804 878931731
    59116804 0}
    2021-12-12T15:42:15.089Z        INFO    mobility/driver mobility/driver.go:344  HO is done successfully: 5929921 to &{87893173159116805 878931731
    59116805 0}
    2021-12-12T15:42:16.082Z        INFO    mobility/driver mobility/driver.go:344  HO is done successfully: 8497897 to &{87893173159116805 878931731
    59116805 0}
    2021-12-12T15:42:16.084Z        INFO    mobility/driver mobility/driver.go:344  HO is done successfully: 5929921 to &{87893173159116802 878931731
    59116802 0}
    2021-12-12T15:42:17.084Z        INFO    mobility/driver mobility/driver.go:344  HO is done successfully: 5929921 to &{87893173159116803 878931731
    59116803 0}
    ```
   
9. Verify whether network policy for Intelligent Connection Management for Automated Handover RI has been created
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get networkpolicies.networking.k8s.io -A -o wide
    NAMESPACE        NAME                                   POD-SELECTOR                                    AGE
    default          block-all-ingress                      <none>                                          23h
    harbor           harbor-network-policy                  app=harbor,component=nginx,release=harbor-app   23h
    kube-system      allow-atomix-controller                name=atomix-controller                          122m
    kube-system      allow-atomix-raft-storage-controller   name=atomix-raft-storage                        122m
    kube-system      allow-onos-operator-app                name=onos-operator-app                          122m
    kube-system      allow-onos-operator-config             name=onos-operator-config                       122m
    kube-system      allow-onos-operator-topo               name=onos-operator-topo                         122m
    smartedge-apps   allow-cm-xapp                          service=cm-xapp                                 122m
    smartedge-apps   allow-onos-ingress                     app=onos                                        122m
    smartedge-apps   onos-consensus-store-0                 app=atomix                                      122m
    ```
  
**Step 4 : Uninstall the Intelligent Connection Management for Automated Handover RI**
  
To uninstall the list of modules deployed by this Reference Implementation, run the following commands.
Note: This will remove all the running pods and the data and configuration stored in the device.

1. To list the package modules, run the below command

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +--------------------------+----------------------------------------------------------+---------+
    |            ID            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```
2. To uninstall the individual module, run the following command with respective module ID
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [............                                      ]  25%
    Successfully removed cm xapp from machine
    Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:11
    Successfully removed sdran from machine
    Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
    Successfully removed network policy from machine
    Cleaning up CM Xapp                                [..................................................] 100%
    Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 30.98 seconds
    Uninstall Finished
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

## ITP/RI/ICMAH/02: Verify ONF portal access for sdran contents with invalid credentials

### Test Summary
  
Verify the ONF portal access with invalid credentials for sdran helm chart during Intelligent Connection Management for Automated Handover RI installation.
  
### Prerequisites
  
Bringup the RI as per [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)
  
### Test Steps

1. Download the RI package from ESH portal and start installation per steps in pre-requisites section.
  
2. During the installation, the user shall be prompted to enter ONF credentials<br>Enter Invalid credentials and verify the script aborts with error as shown below -

    ```shell
    Please contact ONF(https://opennetworking.org/contact/) for username and password credentials that allow access to the sdran helm chart repo.
    Enter sdran username: intel
    Enter sdran password: <Invalid Password>
    Installing CM Xapp dependencies on SE Node . . .   [...........                                       ]  23%  00:01:04
    Unable to add sdran helm chart

    ERROR:
    Unable to add sdran helm chart helm repo add sdran --username intel --password wrong https://sdrancharts.onosproject.org
    Failed to install Intelligent_Connection_Management_for_Automated_Handover took 1 minutes 28.07 seconds
    Installation of package complete
    +--------------------------+----------------------------------------------------------+--------+
    |            Id            |                          Module                          | Status |
    +--------------------------+----------------------------------------------------------+--------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | FAILED |
    +--------------------------+----------------------------------------------------------+--------+
    ```
  
## ITP/RI/ICMAH/03: Verify recovery of single node cluster with Intelligent Connection Management RI from forced reboot

### Test Summary
  
Verify the platform recovery of single node k8s host with Intelligent Connection Management for Automated Handover RI from forced reboot. All pods/service are expected to run and RAN simulator should provide UE/Cells details.
  
### Prerequisites
  
Bringup the RI as per [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)
  
### Test Steps
  
1. Force reboot the Single node k8s host where the Intelligent Connection Management for Automated Handover RI has been installed.<br>Post reboot cycle of the host, the pods status should prompt either 'Running' or 'Completed' as shown below -
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl get pods -A
    NAMESPACE                NAME                                                         READY   STATUS    RESTARTS   AGE
    harbor                   harbor-app-chartmuseum-7cb556754f-hb44g                      1/1     Running   1          35h
    harbor                   harbor-app-core-7486954668-qc2k9                             1/1     Running   1          35h
    harbor                   harbor-app-database-0                                        1/1     Running   1          35h
    harbor                   harbor-app-jobservice-5857d646f-sq2cd                        1/1     Running   1          35h
    harbor                   harbor-app-nginx-65dd6bc7b7-blvp4                            1/1     Running   3          35h
    harbor                   harbor-app-notary-server-5799b54bf6-7v2f2                    1/1     Running   2          35h
    harbor                   harbor-app-notary-signer-5f8d5dfcc9-2dsgc                    1/1     Running   2          35h
    harbor                   harbor-app-portal-88895f59f-5fwp9                            1/1     Running   1          35h
    harbor                   harbor-app-redis-0                                           1/1     Running   1          35h
    harbor                   harbor-app-registry-76546fc777-5n25s                         2/2     Running   2          35h
    harbor                   harbor-app-trivy-0                                           1/1     Running   1          35h
    kube-system              atomix-controller-6767f468cc-4xx87                           1/1     Running   1          34m
    kube-system              atomix-raft-storage-controller-85db5888f6-xp8q4              1/1     Running   1          33m
    kube-system              calico-kube-controllers-6b59cd85f8-9klzg                     1/1     Running   1          35h
    kube-system              calico-node-tvcx5                                            1/1     Running   1          35h
    kube-system              coredns-558bd4d5db-nfx4f                                     1/1     Running   1          35h
    kube-system              coredns-558bd4d5db-xhtzx                                     1/1     Running   1          35h
    kube-system              etcd-ubuntu-4b70b7ba43                                       1/1     Running   1          35h
    kube-system              kube-apiserver-ubuntu-4b70b7ba43                             1/1     Running   1          35h
    kube-system              kube-controller-manager-ubuntu-4b70b7ba43                    1/1     Running   1          35h
    kube-system              kube-multus-ds-amd64-xgk2l                                   1/1     Running   1          35h
    kube-system              kube-proxy-nv4cb                                             1/1     Running   1          35h
    kube-system              kube-scheduler-ubuntu-4b70b7ba43                             1/1     Running   1          35h
    kube-system              onos-operator-app-6864f6f77c-jdj7x                           1/1     Running   1          33m
    kube-system              onos-operator-config-7569c46b76-rh8dn                        1/1     Running   1          33m
    kube-system              onos-operator-topo-7c68bc4d7-rgc4w                           1/1     Running   1          33m
    smartedge-apps           cm-xapp-6d99d58b5-rfqlw                                      1/1     Running   1          31m
    smartedge-apps           onos-cli-764d9697fb-sdx4z                                    1/1     Running   1          32m
    smartedge-apps           onos-consensus-store-0                                       1/1     Running   1          32m
    smartedge-apps           onos-e2t-797bf77554-kk8k5                                    2/3     Running   5          32m
    smartedge-apps           onos-topo-79f7c5c54d-5k6n7                                   2/3     Running   5          32m
    smartedge-apps           onos-uenib-6f7466c87f-b6qfv                                  2/3     Running   5          32m
    smartedge-apps           ran-simulator-55dc5f56c6-c9k6q                               1/1     Running   1          32m
    smartedge-system         nfd-release-node-feature-discovery-master-6c8ff5486d-xs8x2   1/1     Running   1          35h
    smartedge-system         nfd-release-node-feature-discovery-worker-kh7lh              1/1     Running   1          35h
    sriov-network-operator   network-resources-injector-zv6j2                             1/1     Running   1          34h
    sriov-network-operator   operator-webhook-qzv7x                                       1/1     Running   1          34h
    sriov-network-operator   sriov-device-plugin-8b2rm                                    1/1     Running   0          10m
    sriov-network-operator   sriov-network-config-daemon-f28l9                            3/3     Running   3          34h
    sriov-network-operator   sriov-network-operator-68598c6fc6-ttn79                      1/1     Running   1          34h
    telemetry                cadvisor-mknz2                                               2/2     Running   2          35h
    telemetry                collectd-ss2j8                                               3/3     Running   3          35h
    telemetry                grafana-6867674556-cqp8c                                     3/3     Running   3          35h
    telemetry                prometheus-node-exporter-mcwj6                               1/1     Running   1          35h
    telemetry                prometheus-server-5b469cc688-swgx2                           3/3     Running   3          35h
    telemetry                statsd-exporter-cfbd5bf65-jcgc8                              2/2     Running   2          35h
    ```
2. Verify the RAN simulator pods are 'Running' with UE and Cell details.
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get cells
    NCGI                 #UEs Max UEs    TxDB       Lat       Lng Azimuth     Arc   A3Offset     TTT  A3Hyst PCellOffset FreqOffset      PCI    Color
    Idle Conn Neighbors(NCellOffset)
    13842601454c005         0      20   40.00    12.970    77.749     120     120          0       0       0          0          0      122    green
      25,   22, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c004(0)
    13842601454c002         0      20   40.00    12.969    77.753       0     120          0       0       0          0          0      119    green
      2,    1, 13842601454c001(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c004         0      20   40.00    12.971    77.751       0     120          0       0       0          0          0      121    green
      4,   18, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c005(0)
    13842601454c001         0      20   40.00    12.969    77.749       0     120          0       0       0          0          0      118    green
      2,    5, 13842601454c002(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c003         0      20   40.00    12.970    77.754       0     120          0       0       0          0          0      120    green
      9,   12, 13842601454c001(0),13842601454c002(0),13842601454c004(0),13842601454c005(0)
    smartedge-open@ubuntu-4b70b7ba43:~$
    ```

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get ueCount
    100
    ```

## ITP/RI/ICMAH/04: Verify uninstall and install of Intelligent Connection Management for Automated Handover RI
  
### Test Summary
  
Uninstall Intelligent Connection Management for Automated Handover RI and install tha same RI with appropriate product key.
Installation should succeed and RAN simulator should show UE, Cells details.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps
  
1. Verify the installation of ICMAH RI with commands below -

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +--------------------------+----------------------------------------------------------+---------+
    |            ID            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps
    NAME                             READY   STATUS    RESTARTS   AGE
    cm-xapp-6d99d58b5-twk6v          1/1     Running   0          53s
    onos-cli-764d9697fb-clkkm        1/1     Running   0          117s
    onos-consensus-store-0           1/1     Running   0          117s
    onos-e2t-797bf77554-f58rt        3/3     Running   0          117s
    onos-topo-79f7c5c54d-95rfd       3/3     Running   0          117s
    onos-uenib-6f7466c87f-z4dtm      3/3     Running   0          117s
    ran-simulator-55dc5f56c6-2l8gb   1/1     Running   0          72s
    ```

2. Uninstall the Intelligent Connection Management for Automated Handover RI instance.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [............                                      ]  25%
    Successfully removed cm xapp from machine
    Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:11
    Successfully removed sdran from machine
    Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
    Successfully removed network policy from machine
    Cleaning up CM Xapp                                [..................................................] 100%
    Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 31.08 seconds
    Uninstall Finished
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

3. Verify the ICMAH RI is uninstalled successfully

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +----+--------+--------+
    | ID | Module | Status |
    +----+--------+--------+
    +----+--------+--------+
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps
    No resources found in smartedge-apps namespace.
    ```

2. Reinstall the Intelligent Connection Management for Automated Handover RI with valid product key.<br>Installation should succeed and RAN simulator pods should showcase UE, Cell details.
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware install
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  <Valid Product Key>
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    Successfully validated Product Key
    Checking for prerequisites
    W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/security_ubuntu_
    com_ubuntu.list:3
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 1.5%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    ZIP file for module 6022bd8ccc7449002afdbedd already exists. Validating it...
    Module validation passed for 6022bd8ccc7449002afdbedd
    Skipping download...
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    ZIP file for module 619b8bceff6f230021e4409e already exists. Validating it...
    Module validation passed for 619b8bceff6f230021e4409e
    Skipping download...
    Downloading modules completed...
    Installing shared module 'esb_common'
    Unzipping the shared module 'esb_common'...
    running install
    running bdist_egg
    running egg_info
    writing esb_common.egg-info/PKG-INFO
    writing dependency_links to esb_common.egg-info/dependency_links.txt
    writing top-level names to esb_common.egg-info/top_level.txt
    reading manifest file 'esb_common.egg-info/SOURCES.txt'
    writing manifest file 'esb_common.egg-info/SOURCES.txt'
    installing library code to build/bdist.linux-x86_64/egg
    running install_lib
    warning: install_lib: 'build/lib' does not exist -- no Python modules to install

    creating build/bdist.linux-x86_64/egg
    creating build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/PKG-INFO -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/SOURCES.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/dependency_links.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/top_level.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    zip_safe flag not set; analyzing archive contents...
    creating 'dist/esb_common-0.1-py3.8.egg' and adding 'build/bdist.linux-x86_64/egg' to it
    removing 'build/bdist.linux-x86_64/egg' (and everything under it)
    Processing esb_common-0.1-py3.8.egg
    Removing /usr/local/lib/python3.8/dist-packages/esb_common-0.1-py3.8.egg
    Copying esb_common-0.1-py3.8.egg to /usr/local/lib/python3.8/dist-packages
    esb-common 0.1 is already the active version in easy-install.pth

    Installed /usr/local/lib/python3.8/dist-packages/esb_common-0.1-py3.8.egg
    Processing dependencies for esb-common==0.1
    Finished processing dependencies for esb-common==0.1
    Successfully installed shared module 'esb_common'.
    Modules to be installed by package are ['Intelligent_Connection_Management_for_Automated_Handover']
    Installing Intelligent_Connection_Management_for_Automated_Handover
    Verifying SE Node (xx.xxx.xxx.xxx)                  [..................................................] 100%


    Before installing freshly, deleting partially installed pods if any ...
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp quietly                        [..................................................] 100%


    Please contact ONF(https://opennetworking.org/contact/) for username and password credentials that allow access to the sdran helm chart repo.
    Enter sdran username: intel
    Enter sdran password:
    Installing CM Xapp dependencies on SE Node . . .   [..................................................] 100%
    Successfully installed: SDRAN

    CM Xapp installation started. This might take upto 1 mins
    Installing CM Xapp                                 [..................................................] 100%
    Successfully installed: CM Xapp

    Verifying CM Xapp installation in (xx.xxx.xxx.xxx)  [..................................................] 100%
    Successfully installed Intelligent_Connection_Management_for_Automated_Handover took 4 minutes 0.25 seconds
    Installation of package complete
    ***Recommended to reboot system after installation***
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

3. Verify the installation with commands below

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +--------------------------+----------------------------------------------------------+---------+
    |            ID            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps
    NAME                             READY   STATUS    RESTARTS   AGE
    cm-xapp-6d99d58b5-jchmt          1/1     Running   0          68s
    onos-cli-764d9697fb-p8f27        1/1     Running   0          2m2s
    onos-consensus-store-0           1/1     Running   0          2m2s
    onos-e2t-797bf77554-q6hj2        3/3     Running   0          2m2s
    onos-topo-79f7c5c54d-n45dr       3/3     Running   0          2m2s
    onos-uenib-6f7466c87f-z2fbp      3/3     Running   0          2m2s
    ran-simulator-55dc5f56c6-7x258   1/1     Running   0          86s
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-p8f27 -- onos ransim get ueCount
    100
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-p8f27 -- onos ransim get cells
    NCGI                 #UEs Max UEs    TxDB       Lat       Lng Azimuth     Arc   A3Offset     TTT  A3Hyst PCellOffset FreqOffset      PCI    Color Idle Conn Neighbors(NCellOffset)
    13842601454c002         0      20   40.00    12.969    77.753       0     120          0       0       0          0          0      119    green    8,    0, 13842601454c001(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c003         0      20   40.00    12.970    77.754       0     120          0       0       0          0          0      120    green   14,   11, 13842601454c001(0),13842601454c002(0),13842601454c004(0),13842601454c005(0)
    13842601454c005         0      20   40.00    12.970    77.749     120     120          0       0       0          0          0      122    green   14,   12, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c004(0)
    13842601454c001         0      20   40.00    12.969    77.749       0     120          0       0       0          0          0      118    green   12,    6, 13842601454c002(0),13842601454c003(0),13842601454c004(0),13842601454c005(0)
    13842601454c004         0      20   40.00    12.971    77.751       0     120          0       0       0          0          0      121    green   16,    7, 13842601454c001(0),13842601454c002(0),13842601454c003(0),13842601454c005(0)
    ```
## ITP/RI/ICMAH/05: Delete Intelligent Connection Management application pod and verify its recovery and functionality

### Test Summary
  
Delete the Intelligent Connection Management for Automated Handover application pods and verify its recovery and functionality by accessing the individuals pods/logs.
  
### Prerequisites
  
Bringup the RI as per [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)
  
### Test Steps
  
1. Verify the ICMAH RI application pods with command below
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl get pods -n smartedge-apps
    smartedge-apps           cm-xapp-6d99d58b5-rfqlw                                      1/1     Running   1          39m
    smartedge-apps           onos-cli-764d9697fb-sdx4z                                    1/1     Running   1          40m
    smartedge-apps           onos-consensus-store-0                                       1/1     Running   1          40m
    smartedge-apps           onos-e2t-797bf77554-kk8k5                                    2/3     Running   6          40m
    smartedge-apps           onos-topo-79f7c5c54d-5k6n7                                   2/3     Running   6          40m
    smartedge-apps           onos-uenib-6f7466c87f-b6qfv                                  2/3     Running   6          40m
    smartedge-apps           ran-simulator-55dc5f56c6-c9k6q                               1/1     Running   1          40m
    ```  
2. Delete the CM xApps and RAN simulator pod from 'smartedge-apps' namespace 
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl delete pod -n smartedge-apps cm-xapp-6d99d58b5-rfqlw
    pod "cm-xapp-6d99d58b5-rfqlw" deleted
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl delete pod -n smartedge-apps ran-simulator-55dc5f56c6-c9k6q
    pod "ran-simulator-55dc5f56c6-c9k6q" deleted
    ```
3. Verify the deleted pod recovers with refreshed UE connection status

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl get pods -n smartedge-apps
    NAME                             READY   STATUS    RESTARTS   AGE
    cm-xapp-6d99d58b5-89dwd          1/1     Running   0          37s
    onos-cli-764d9697fb-sdx4z        1/1     Running   1          41m
    onos-consensus-store-0           1/1     Running   1          41m
    onos-e2t-797bf77554-kk8k5        2/3     Running   6          41m
    onos-topo-79f7c5c54d-5k6n7       2/3     Running   6          41m
    onos-uenib-6f7466c87f-b6qfv      2/3     Running   6          41m
    ran-simulator-55dc5f56c6-tq57b   0/1     Running   0          20s
    ```
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get ueCount
    100
    ```
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get ues | grep IDLE | wc -l
    76
    ```

## ITP/RI/ICMAH/06: Verify Product key integrity during ICMAH installation
  
### Test Summary

Intelligent Connection Management for Automated Handover RI Installation should fail for an input of invalid Product key

### Prerequisites

- SEO DEK deployed on target host
- Intelligent Connection Management for Automated Handover RI downloaded
 
### Test Steps

1. During the installation, user shall be prompted for the Product Key. Enter invalid Product key and verify the installation fails with error as below.

    ```shell
    smartedge-open@ubuntu-c1c5dc0185:~/Intelligent_Connection_Management$ ./edgesoftware install
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  12345678-1234-4321-098
    765432112
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    [WARNING] Invalid Product Key. Continuing installation with local files
    Checking for prerequisites
    ```
    ```shell
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 1.5%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    Failed to download the module esb_common. 401 Unauthorized
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    Failed to download the module Intelligent_Connection_Management_for_Automated_Handover. 401 Unauthorized
    Downloading modules completed...
    Installing shared module 'esb_common'
    Failed to find shared module 'esb_common'. Exiting installation.
    ```

## ITP/RI/ICMAH/07: Verify reinstallation of Intelligent Connection Management for Automated Handover RI
  
### Test Summary
  
Re-install Intelligent Connection Management for Automated Handover RI in an already installed node<br>Install -> Install

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps
  
1. Re-install Intelligent Connection Management for Automated Handover RI again in the same node, after the previous installation is success.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware install                                           [655/2000]
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  <Product Key>
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    Successfully validated Product Key
    Checking for prerequisites
    ...
    ...
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 2.4%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    ZIP file for module 6022bd8ccc7449002afdbedd already exists. Validating it...
    Module validation passed for 6022bd8ccc7449002afdbedd
    Skipping download...
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    ZIP file for module 619b8bceff6f230021e4409e already exists. Validating it...
    Module validation passed for 619b8bceff6f230021e4409e
    Skipping download...
    Downloading modules completed...
    Installing shared module 'esb_common'
    Unzipping the shared module 'esb_common'...
    running install
    ```

2. During re-installation the script shall prompt user to confirm with option 'YES' or 'NO'.<br>Enter 'YES' to proceed with re-installation.

    ```shell
    Installed /usr/local/lib/python3.8/dist-packages/esb_common-0.1-py3.8.egg                                                              [161/2000]
    Processing dependencies for esb-common==0.1
    Finished processing dependencies for esb-common==0.1
    Successfully installed shared module 'esb_common'.
    Modules to be installed by package are ['Intelligent_Connection_Management_for_Automated_Handover']
    Verifying CM Xapp installation in ()               [..................................................] 100%
    Intelligent_Connection_Management_for_Automated_Handover is already installed. Type YES to reinstall or NO to skip installation.
    YES
    Installing Intelligent_Connection_Management_for_Automated_Handover
    Verifying SE Node (xx.xxx.xxx.xxx)                  [..................................................] 100%

    Successfully re-installed: SDRAN
    CM Xapp installation started. This might take upto 1 mins
    Installing CM Xapp                                 [..................................................] 100%
    Successfully re-installed: CM Xapp

    Verifying CM Xapp installation in (xx.xxx.xxx.xxx)  [..................................................] 100%
    Successfully installed Intelligent_Connection_Management_for_Automated_Handover took 28.92 seconds
    Installation of package complete
    ***Recommended to reboot system after installation***
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

3. Verify the pods status prompt either 'Running' or 'Completed' after re-installation of RI 
  
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -A
    NAMESPACE                NAME                                                         READY   STATUS    RESTARTS   AGE
    harbor                   harbor-app-chartmuseum-7cb556754f-hb44g                      1/1     Running   1          35h
    harbor                   harbor-app-core-7486954668-qc2k9                             1/1     Running   1          35h
    harbor                   harbor-app-database-0                                        1/1     Running   1          35h
    harbor                   harbor-app-jobservice-5857d646f-sq2cd                        1/1     Running   1          35h
    harbor                   harbor-app-nginx-65dd6bc7b7-blvp4                            1/1     Running   3          35h
    harbor                   harbor-app-notary-server-5799b54bf6-7v2f2                    1/1     Running   2          35h
    harbor                   harbor-app-notary-signer-5f8d5dfcc9-2dsgc                    1/1     Running   2          35h
    harbor                   harbor-app-portal-88895f59f-5fwp9                            1/1     Running   1          35h
    harbor                   harbor-app-redis-0                                           1/1     Running   1          35h
    harbor                   harbor-app-registry-76546fc777-5n25s                         2/2     Running   2          35h
    harbor                   harbor-app-trivy-0                                           1/1     Running   1          35h
    kube-system              atomix-controller-6767f468cc-4xx87                           1/1     Running   1          67m
    kube-system              atomix-raft-storage-controller-85db5888f6-xp8q4              1/1     Running   1          66m
    kube-system              calico-kube-controllers-6b59cd85f8-9klzg                     1/1     Running   1          35h
    kube-system              calico-node-tvcx5                                            1/1     Running   1          35h
    kube-system              coredns-558bd4d5db-nfx4f                                     1/1     Running   1          35h
    kube-system              coredns-558bd4d5db-xhtzx                                     1/1     Running   1          35h
    kube-system              etcd-ubuntu-4b70b7ba43                                       1/1     Running   1          35h
    kube-system              kube-apiserver-ubuntu-4b70b7ba43                             1/1     Running   1          35h
    kube-system              kube-controller-manager-ubuntu-4b70b7ba43                    1/1     Running   1          35h
    kube-system              kube-multus-ds-amd64-xgk2l                                   1/1     Running   1          35h
    kube-system              kube-proxy-nv4cb                                             1/1     Running   1          35h
    kube-system              kube-scheduler-ubuntu-4b70b7ba43                             1/1     Running   1          35h
    kube-system              onos-operator-app-6864f6f77c-jdj7x                           1/1     Running   1          66m
    kube-system              onos-operator-config-7569c46b76-rh8dn                        1/1     Running   1          66m
    kube-system              onos-operator-topo-7c68bc4d7-rgc4w                           1/1     Running   1          66m
    smartedge-apps           cm-xapp-6d99d58b5-89dwd                                      1/1     Running   0          25m
    smartedge-apps           onos-cli-764d9697fb-sdx4z                                    1/1     Running   1          66m
    smartedge-apps           onos-consensus-store-0                                       1/1     Running   1          66m
    smartedge-apps           onos-e2t-797bf77554-kk8k5                                    2/3     Running   11         66m
    smartedge-apps           onos-topo-79f7c5c54d-5k6n7                                   2/3     Running   11         66m
    smartedge-apps           onos-uenib-6f7466c87f-b6qfv                                  2/3     Running   11         66m
    smartedge-apps           ran-simulator-55dc5f56c6-tq57b                               1/1     Running   0          24m
    smartedge-system         nfd-release-node-feature-discovery-master-6c8ff5486d-xs8x2   1/1     Running   1          35h
    smartedge-system         nfd-release-node-feature-discovery-worker-kh7lh              1/1     Running   1          35h
    sriov-network-operator   network-resources-injector-zv6j2                             1/1     Running   1          35h
    sriov-network-operator   operator-webhook-qzv7x                                       1/1     Running   1          35h
    sriov-network-operator   sriov-device-plugin-8b2rm                                    1/1     Running   0          43m
    sriov-network-operator   sriov-network-config-daemon-f28l9                            3/3     Running   3          35h
    sriov-network-operator   sriov-network-operator-68598c6fc6-ttn79                      1/1     Running   1          35h
    telemetry                cadvisor-mknz2                                               2/2     Running   2          35h
    telemetry                collectd-ss2j8                                               3/3     Running   3          35h
    telemetry                grafana-6867674556-cqp8c                                     3/3     Running   3          35h
    telemetry                prometheus-node-exporter-mcwj6                               1/1     Running   1          35h
    telemetry                prometheus-server-5b469cc688-swgx2                           3/3     Running   3          35h
    telemetry                statsd-exporter-cfbd5bf65-jcgc8                              2/2     Running   2          35h
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get ues | grep CONNECTED | wc -l
    56
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl exec -it -n smartedge-apps onos-cli-764d9697fb-sdx4z -- onos ransim get ueCount
    100
    ```  
  
## ITP/RI/ICMAH/08: Verify ICMAH RI installation with product key of another RI instance
  
### Test Summary
  
Install Intelligent Connection Management for Automated Handover RI with product key of another RI instance.<br>RI installation should fail.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps

1. Verify installation of ICMAH RI with product key of another RI.<br> Installation should fail displaying invalid product key.   
  
    ```shell
    smartedge-open@ubuntu-c1c5dc0185:~/Intelligent_Connection_Management$ ./edgesoftware install
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  8745563b-e7ae-4e43-8a3
    6-0559c4258818
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    [WARNING] Invalid Product Key. Continuing installation with local files
    Checking for prerequisites
    ```
    ```shell
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 1.5%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    Failed to download the module esb_common. 401 Unauthorized
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    Failed to download the module Intelligent_Connection_Management_for_Automated_Handover. 401 Unauthorized
    Downloading modules completed...
    Installing shared module 'esb_common'
    Failed to find shared module 'esb_common'. Exiting installation.
    ```

## ITP/RI/ICMAH/09: Verify uninstall and install of ICMAH RI with an invalid product key
  
### Test Summary
  
Uninstall Intelligent Connection Management for Automated Handover RI and install tha same RI with invalid product key.
Installation process should abort for invalid product key credentials.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps
  
1. Uninstall the Intelligent Connection Management for Automated Handover RI instance.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [............                                      ]  25%
    Successfully removed cm xapp from machine
    Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:11
    Successfully removed sdran from machine
    Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
    Successfully removed network policy from machine
    Cleaning up CM Xapp                                [..................................................] 100%
    Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 31.38 seconds
    Uninstall Finished
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +----+--------+--------+
    | ID | Module | Status |
    +----+--------+--------+
    +----+--------+--------+
    ```

2. Reinstall the Intelligent Connection Management for Automated Handover RI with invalid product key.<br>Installation should fail displaying invalid product key.
  
    ```shell
    TBD: Pending JIRA closure
    ```

## ITP/RI/ICMAH/10: Verify uninstall of ICMAH RI followed by an abort signal for previous cleanup instance
  
### Test Summary
  
Verify the uninstall of ICMAH RI followed by an abort signal for previous interrupted cleanup instance.<br>Uninstall should succeed irrespective of previous cleanup state.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps

1. Verify the ICMAH RI installation with list command

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list

    +--------------------------+----------------------------------------------------------+---------+
    |            ID            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$
    ```

2. Start the uninstall process of ICMAH RI instance with module id, abort the process with Ctrl+C before it completes.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [............                                      ]  25%^CUninstallation aborted by user. Exiting uninstallation
    ```

3. Verify the uninstall is aborted and ICMAH RI instance exists.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ kubectl get pods -n smartedge-apps
    NAME                             READY   STATUS    RESTARTS   AGE
    onos-cli-764d9697fb-cn954        1/1     Running   0          79m
    onos-consensus-store-0           1/1     Running   0          79m
    onos-e2t-797bf77554-7gwtk        3/3     Running   0          79m
    onos-topo-79f7c5c54d-4bzcs       3/3     Running   0          79m
    onos-uenib-6f7466c87f-hrmlz      3/3     Running   0          79m
    ran-simulator-55dc5f56c6-d9wh5   1/1     Running   0          78m
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +--------------------------+----------------------------------------------------------+---------+
    |            ID            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

4. Re-trigger the uninstall process again with './edgesoftware uninstall <modulle id>' command.<br>Ensure the uninstall is Success by checking the pods in 'smartedge-apps' namespace.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:10
    Successfully removed sdran from machine
    Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
    Successfully removed network policy from machine
    Cleaning up CM Xapp                                [..................................................] 100%
    Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 30.93 seconds
    Uninstall Finished
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware list
    +----+--------+--------+
    | ID | Module | Status |
    +----+--------+--------+
    +----+--------+--------+
    ```

## ITP/RI/ICMAH/11: Verify ICMAH RI installation with an invalid credentials for ONF portal after successful install and uninstall cycle
  
### Test Summary
  
Verify the Intelligent Connection Management for Automated Handover RI installation with invalid credentials for ONF portal after successful install and uninstall of RI cycle once. Script should prompt error for invalid input.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps

1. Uninstall the Intelligent Connection Management for Automated Handover RI instance.

    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware uninstall 619b8bceff6f230021e4409e
    Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
    Uninstalling Intelligent_Connection_Management_for_Automated_Handover
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp                                [............                                      ]  25%
    Successfully removed cm xapp from machine
    Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:11
    Successfully removed sdran from machine
    Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
    Successfully removed network policy from machine
    Cleaning up CM Xapp                                [..................................................] 100%
    Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 31.38 seconds
    Uninstall Finished
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```

2. Start the installation of Intelligent Connection Management for Automated Handover RI again with valid product key.<br>Enter invalid password for ONF portal and verify the installation fails with error shown below

    ```shell
      Please contact ONF(https://opennetworking.org/contact/) for username and password credentials that allow access to the sdran helm chart repo.
      Enter sdran username: intel
      Enter sdran password: <Invalid Password>
      Installing CM Xapp dependencies on SE Node . . .   [...........                                       ]  23%  00:01:04
      Unable to add sdran helm chart

      ERROR:
      Unable to add sdran helm chart helm repo add sdran --username intel --password wrong https://sdrancharts.onosproject.org
      Failed to install Intelligent_Connection_Management_for_Automated_Handover took 1 minutes 28.07 seconds
      Installation of package complete
      +--------------------------+----------------------------------------------------------+--------+
      |            Id            |                          Module                          | Status |
      +--------------------------+----------------------------------------------------------+--------+
      | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | FAILED |
      +--------------------------+----------------------------------------------------------+--------+
      ```

## ITP/RI/ICMAH/12: Verify E2E Latency measurement of CMxApp meets the ORAN KPI using OPENVINO 

### Test Summary
Verify E2E Latency measurement of Intelligent Connection Management for Automated Handover RI meets the ORAN KPI using OPENVINO method. Handover request processing time should be less than 0.01 second.
    
### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps

1. Verify the CMxApp pod status with the command below

    ```shell
    smartedge-open@@ubuntu-4b70b7ba43:~$ kubectl -n smartedge-apps get pod
    NAME                             READY   STATUS    RESTARTS   AGE
    cm-xapp-6d99d58b5-2l4t2          1/1     Running   0          20h
    onos-cli-764d9697fb-dpg5b        1/1     Running   0          20h
    onos-consensus-store-0           1/1     Running   0          20h
    onos-e2t-df496c8cd-qhjw7         3/3     Running   0          20h
    onos-topo-79f7c5c54d-fgvbj       3/3     Running   0          20h
    onos-uenib-6f7466c87f-qs9r4      3/3     Running   0          20h
    ran-simulator-55dc5f56c6-fjc5k   1/1     Running   0          20h
    ```
2. Verify  Handover request processing time with CMxApp and RAN simulator pod from 'smartedge-apps' namespace 

   Note: Minimum active UE number should be 50 and maximum number of UE 100 or 150. The total running time will be more than 4 hours and 99% the total Handover request processing time should be less than 0.01 second. 
         If total Handover request processing time is more than 0.01 second, uninstall and reinstall the package and repeat the process.

	```shell
	smartedge-open@@ubuntu-4b70b7ba43:~$ kubectl logs cm-xapp-6d99d58b5-2l4t2 -n smartedge-apps -c cm-xapp
	02/24/2022 05:11:57 AM Calling control req no 1 for UE : 9438026 Serving cell: 13842601454c002 target_cell 13842601454c001
	02/24/2022 05:11:57 AM Number of Active UEs: 14
	02/24/2022 05:11:57 AM Number of total UEs: 64
	02/24/2022 05:11:57 AM HO processing time: 0.0065 seconds
	02/24/2022 05:11:57 AM Queue len: 4
	02/24/2022 05:11:57 AM Queue len: 3
	02/24/2022 05:11:57 AM Calling control req no 2 for UE : 9104113 Serving cell: 13842601454c006 target_cell 13842601454c001
	02/24/2022 05:11:57 AM Number of Active UEs: 14
	02/24/2022 05:11:57 AM Number of total UEs: 64
	02/24/2022 05:11:57 AM HO processing time: 0.0088 seconds
	02/24/2022 05:11:57 AM Queue len: 1
	02/24/2022 05:11:57 AM Queue len: 1
	02/24/2022 05:11:57 AM Calling control req no 3 for UE : 7437845 Serving cell: 13842601454c002 target_cell 13842601454c006
	02/24/2022 05:11:57 AM Number of Active UEs: 14
	02/24/2022 05:11:57 AM Number of total UEs: 64
	02/24/2022 05:11:57 AM HO processing time: 0.0048 seconds
	02/24/2022 05:11:58 AM Queue len: 1
	02/24/2022 05:11:58 AM Calling control req no 4 for UE : 3697252 Serving cell: 13842601454c002 target_cell 13842601454c006
	02/24/2022 05:11:58 AM Number of Active UEs: 14
	02/24/2022 05:11:58 AM Number of total UEs: 64
	02/24/2022 05:11:58 AM HO processing time: 0.0057 seconds
	02/24/2022 05:11:58 AM Queue len: 1
	02/24/2022 05:11:58 AM Queue len: 1
	02/24/2022 05:11:58 AM Calling control req no 5 for UE : 1745205 Serving cell: 13842601454c001 target_cell 13842601454c006
	02/24/2022 05:11:58 AM Number of Active UEs: 14
	02/24/2022 05:11:58 AM Number of total UEs: 65
	02/24/2022 05:11:58 AM HO processing time: 0.0056 seconds
	02/24/2022 05:11:58 AM Queue len: 1
	02/24/2022 05:11:58 AM Calling control req no 6 for UE : 1542662 Serving cell: 13842601454c007 target_cell 13842601454c001
	02/24/2022 05:11:58 AM Number of Active UEs: 14
	02/24/2022 05:11:58 AM Number of total UEs: 65
	02/24/2022 05:11:58 AM HO processing time: 0.0068 seconds
	02/24/2022 05:11:58 AM Queue len: 1
	02/24/2022 05:11:59 AM Queue len: 1
	02/24/2022 05:11:59 AM Queue len: 1
	02/24/2022 05:12:01 AM Queue len: 1
	02/24/2022 05:12:01 AM Queue len: 1
	02/24/2022 05:12:02 AM Queue len: 1
	02/24/2022 05:12:02 AM Calling control req no 7 for UE : 4704529 Serving cell: 13842601454c002 target_cell 13842601454c001
	02/24/2022 05:12:02 AM Number of Active UEs: 14
	02/24/2022 05:12:02 AM Number of total UEs: 66
	02/24/2022 05:12:02 AM HO processing time: 0.0077 seconds
	02/24/2022 05:12:02 AM Queue len: 1
	02/24/2022 05:12:03 AM Queue len: 1
	02/24/2022 05:12:04 AM Queue len: 1
	02/24/2022 05:12:05 AM Queue len: 1
	02/24/2022 05:12:05 AM Total Indications: 12000 Periodic: 6936 Event-Based: 4992 RRC: 72
	02/24/2022 05:12:06 AM Queue len: 1
	02/24/2022 05:12:07 AM Queue len: 1
	02/24/2022 05:12:07 AM Calling control req no 8 for UE : 8560154 Serving cell: 13842601454c002 target_cell 13842601454c001
	02/24/2022 05:12:07 AM Number of Active UEs: 14
	02/24/2022 05:12:07 AM Number of total UEs: 67
	02/24/2022 05:12:07 AM HO processing time: 0.0064 seconds
	02/24/2022 05:12:07 AM Queue len: 1
	02/24/2022 05:12:08 AM Queue len: 1
	02/24/2022 05:12:08 AM Queue len: 1
	02/24/2022 05:12:08 AM Queue len: 1
	02/24/2022 05:12:08 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:09 AM Queue len: 1
	02/24/2022 05:12:10 AM Queue len: 1
	02/24/2022 05:12:10 AM Queue len: 1
	02/24/2022 05:12:10 AM Queue len: 1
	02/24/2022 05:12:10 AM Queue len: 1
	02/24/2022 05:12:10 AM Queue len: 1
	02/24/2022 05:12:10 AM Calling control req no 9 for UE : 7437845 Serving cell: 13842601454c006 target_cell 13842601454c003
	02/24/2022 05:12:11 AM Number of Active UEs: 15
	02/24/2022 05:12:11 AM Number of total UEs: 67
	02/24/2022 05:12:11 AM HO processing time: 0.0045 seconds
	02/24/2022 05:12:11 AM Queue len: 1
	02/24/2022 05:12:11 AM Queue len: 1
	```
    Note: Handover request processing time should be less than 0.01 second

3. After latency measurement process, execute the following command to get xapp log
  
   ```shell
   smartedge-open@ubuntu-4b70b7ba43:~$ kubectl -n smartedge-apps exec -it cm-xapp-6d99d58b5-2l4t2  -- bash
   Defaulted container "cm-xapp" out of: cm-xapp, onos-proxy
   openvino@cm-xapp-cbb7b9499-gnk2q:~$ ls
   HOprocess.py  __pycache__     cDQNandGNN.py  databaseProcess.py  oranHandOverEnv.py       queueManagement.py  xApp_ONF.py
   OpenVINO      cActivation.py  csrc           onos_sdk_client.so  pygo_mediation_layer.py  weights.data        xapp.log
   ```
4. Verify the xapp log file name using below command and dump logs as log.txt
      
    ```shell
   smartedge-open@ubuntu-4b70b7ba43:/home/smartedge-open/dek/tmp$ kubectl cp smartedge-apps/cm-xapp-6d99d58b5-2l4t2:/home/openvino/xapp.log ./log.txt
   Defaulted container "cm-xapp" out of: cm-xapp, onos-proxy
   smartedge-open@esi101:/home/smartedge-open/dek/tmp$ ls
    log.txt
     ```
5. Download the Python package from the below repo
	
    ```shell	
    git clone https://github.com/intel-innersource/networking.wireless.oran-ric.xapp-icmah/blob/master/ORAN_sim_ONF/latest.py
    ```	
	
6. Execute the following command from Python path
	
Note: Minimum active UE number should be 50 and maximum number of UE 100 or 150. The total running time will be more than 4 hours and 99% the total Handover request    	processing time should be less than 0.01 second.
Python file will store the numbers and when we run latest.py, it will plot a graphs to verify Handover request processing time.
	 
 ```shell
 smartedge-open@ubuntu-4b70b7ba43:/home/smartedge-open/dek/tmp1:$ python3 latest.py
 ```
   ![image](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/b08d04c7-872d-4408-a709-a5cf8a575e12)


7. Validating the latency measurement
   
Latency measurements are deduced based on Handover request processing time and the expectation is to be less than 0.01 second. Towards it the user has to check UE/Handover request and sort the Handover request processing time in csv format file. per the tabulated info a graph shall be plotted to verify Handover request processing time.
  ![HOprocesstime_1](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/bbec4eea-da71-4da9-b9d2-18381c61cec4)
  ![QueueSize](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/7f623adf-b138-4020-a24c-a7351f55eebf)

## ITP/RI/ICMAH/13: Verify E2E Latency measurement of CMxApp meets the ORAN KPI using Python

### Test Summary

Verify E2E Latency measurement of Intelligent Connection Management for Automated Handover RI meets the ORAN KPI using Python. 99% of occurences the Handover request processing time should be less than 0.1 to 0.15 seconds.

### Prerequisites
  
Start RI Installation (./edgesoftware install) [ITP/RI/ICMAH/01: Intelligent Connection Management for Automated Handover RI Installation and Verification](#itpriicmah01-Intelligent-Connection-Management-for-Automated-Handover-RI-Installation-and-Verification)

### Test Steps

Step 1. Uninstall the RI package by using the below command
Note: For verifying latency measurement for python method, need to modify the parameters. so uninstall the edgesoftware and do the changes.
	
	```shell
	./edgesoftware uninstall -a
	```
	```shell	
	smartedge-open@ubuntu-4b70b7ba43:/home/smartedge-open/Intelligent_Connection_Management$ ./edgesoftware uninstall -a
	Components to be uninstalled are :['Intelligent_Connection_Management_for_Automated_Handover']
	Uninstalling Intelligent_Connection_Management_for_Automated_Handover
	Uninstalling CM Xapp This might take upto 5 minutes.
	Cleaning up CM Xapp                                [............                                      ]  25%
	Successfully removed cm xapp from machine
	Cleaning up CM Xapp                                [.........................                         ]  50%  00:00:11
	Successfully removed sdran from machine
	Cleaning up CM Xapp                                [.....................................             ]  75%  00:00:07
	Successfully removed network policy from machine
	Cleaning up CM Xapp                                [..................................................] 100%
	Successfully uninstalled Intelligent_Connection_Management_for_Automated_Handover took 30.87 seconds
	Uninstall Finished
	+--------------------------+----------------------------------------------------------+---------+
	|            Id            |                          Module                          |  Status |
	+--------------------------+----------------------------------------------------------+---------+
	| 61d80982d534850021b1422d | Intelligent Connection Management for Automated Handover | SUCCESS |
	+--------------------------+----------------------------------------------------------+---------+
	```

	Step 2. Set the following parameters from below path
	```shell
	Intelligent_Connection_Management/Intelligent_Connection_Management_for_Automated_Handover_2.0.0/Intelligent_Connection_Management_for_Automated_Handover/CM-Xapp/cm- xapp/values.yaml
	```
	```shell	
	parallelLoop=false --qValue=0 --preprocessing=true 
	```
	
**Step 3 : Reinstall the Intelligent Connection Management for Automated Handover RI with valid product key **.

1. Run the command below to install the Reference Implementation:
   
  ```shell
  $ ./edgesoftware install
  ```

2. During the installation, user shall be prompted for the Product Key. The Product Key is contained in the email you received from Intel confirming your download.
 
    ```shell
    smartedge-open@ubuntu-4b70b7ba43:~/Intelligent_Connection_Management$ ./edgesoftware install
    Please enter the Product Key. The Product Key is contained in the email you received from Intel confirming your download:  <Product-Key>
    Starting the setup...
    ESB CLI version: 2021.4
    Target OS: Ubuntu 20.04
    Python version: 3.8.10
    Checking Internet connection
    Connected to the Internet
    Validating product key
    Successfully validated Product Key
    Checking for prerequisites
    ```

    ```shell
    --------Succesfuly installed prerequisites--------
    All dependencies met
    -------------------SYSTEM INFO--------------------
    Package Name: Intelligent Connection Management for Automated Handover 2.0.0
    Product Name: Dell Inc. PowerEdge R750
    CPU SKU: Intel(R) Xeon(R) Gold 6338N CPU @ 2.20GHz
    Memory Size: 504 GB
    Operating System: Ubuntu 20.04.2 LTS
    Kernel Version: 5.13.0-27-generic
    Accelerator: None
    CPU Utilization: 1.2%
    Available Disk Space: 433 GB
    Starting installation
    Downloading modules...
    Downloading component esb_common
    100%|██████████████████████████████████████████████████████████████████████████████████████████████████████| 44.0M/44.0M [00:43<00:00, 1.01MiB/s]
    Module validation passed for 6022bd8ccc7449002afdbedd
    Successfully downloaded module esb_common
    Downloading component Intelligent_Connection_Management_for_Automated_Handover
    100%|███████████████████████████████████████████████████████████████████████████████████████████████████████| 1.95M/1.95M [00:02<00:00, 951kiB/s]
    Module validation passed for 619b8bceff6f230021e4409e
    Successfully downloaded module Intelligent_Connection_Management_for_Automated_Handover
    Downloading modules completed...
    Installing shared module 'esb_common'
    Unzipping the shared module 'esb_common'...
    running install
    running bdist_egg
    running egg_info
    creating esb_common.egg-info
    writing esb_common.egg-info/PKG-INFO
    writing dependency_links to esb_common.egg-info/dependency_links.txt
    writing top-level names to esb_common.egg-info/top_level.txt
    writing manifest file 'esb_common.egg-info/SOURCES.txt'
    reading manifest file 'esb_common.egg-info/SOURCES.txt'
    writing manifest file 'esb_common.egg-info/SOURCES.txt'
    installing library code to build/bdist.linux-x86_64/egg
    ```

    ```shell
    creating build
    creating build/bdist.linux-x86_64
    creating build/bdist.linux-x86_64/egg
    creating build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/PKG-INFO -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/SOURCES.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/dependency_links.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    copying esb_common.egg-info/top_level.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
    zip_safe flag not set; analyzing archive contents...
    creating dist
    creating 'dist/esb_common-0.1-py3.8.egg' and adding 'build/bdist.linux-x86_64/egg' to it
    removing 'build/bdist.linux-x86_64/egg' (and everything under it)
    Processing esb_common-0.1-py3.8.egg
    Copying esb_common-0.1-py3.8.egg to /usr/local/lib/python3.8/dist-packages
    Adding esb-common 0.1 to easy-install.pth file

    Installed /usr/local/lib/python3.8/dist-packages/esb_common-0.1-py3.8.egg
    Processing dependencies for esb-common==0.1
    Finished processing dependencies for esb-common==0.1
    Successfully installed shared module 'esb_common'.
    Installing Lanternrock SDK
    Successfully installed Lanternrock SDK.
    Unzipping the module Intelligent_Connection_Management_for_Automated_Handover...
    Modules to be installed by package are ['Intelligent_Connection_Management_for_Automated_Handover']
    Installing Intelligent_Connection_Management_for_Automated_Handover
    Verifying SE Node (xx.xxx.xxx.xxx)                  [..................................................] 100%


    Before installing freshly, deleting partially installed pods if any ...
    Uninstalling CM Xapp This might take upto 5 minutes.
    Cleaning up CM Xapp quietly                        [..................................................] 100%
    ```

3. During the installation, user shall be prompted to enter username and password for ONF portal to download SDRAN helm chart.

    ```shell
    Please contact ONF(https://opennetworking.org/contact/) for username and password credentials that allow access to the sdran helm chart repo.
    Enter sdran username: intel
    Enter sdran password: <ONF Password>
    Installing CM Xapp dependencies on SE Node . . .   [..................................................] 100%
    Successfully installed: SDRAN
    ```
  
4. When the installation is complete, you shall see the message **Installation of package complete** with the installation status for each module.

    ```shell
    CM Xapp installation started. This might take upto 1 mins
    Installing CM Xapp                                 [..................................................] 100%
    Successfully installed: CM Xapp

    Verifying CM Xapp installation in (xx.xxx.xxx.xxx)  [..................................................] 100%
    Successfully installed Intelligent_Connection_Management_for_Automated_Handover took 13 minutes 58.31 seconds
    Installation of package complete
    ***Recommended to reboot system after installation***
    +--------------------------+----------------------------------------------------------+---------+
    |            Id            |                          Module                          |  Status |
    +--------------------------+----------------------------------------------------------+---------+
    | 619b8bceff6f230021e4409e | Intelligent Connection Management for Automated Handover | SUCCESS |
    +--------------------------+----------------------------------------------------------+---------+
    ```
**Note:** Installation logs are available at path: /var/log/esb-cli/Intelligent_Connection_Management_for_Automated_Handover_1.0.0/Intelligent_Connection_Management_for_Automated_Handover/install.log
	
Step 5. Download the python package from the below repo

  ```shell	
  git clone https://github.com/intel-innersource/networking.wireless.oran-ric.xapp-icmah/blob/master/ORAN_sim_ONF/latest.py
  ```	
Step 6. Verify the CMxApp pod status with the command below
	
  ```shell
  smartedge-open@@ubuntu-4b70b7ba43:~$ kubectl -n smartedge-apps get pod
    NAME                             READY   STATUS    RESTARTS   AGE
    cm-xapp-6d99d58b5-2l4t2          1/1     Running   0          20h
    onos-cli-764d9697fb-dpg5b        1/1     Running   0          20h
    onos-consensus-store-0           1/1     Running   0          20h
    onos-e2t-df496c8cd-qhjw7         3/3     Running   0          20h
    onos-topo-79f7c5c54d-fgvbj       3/3     Running   0          20h
    onos-uenib-6f7466c87f-qs9r4      3/3     Running   0          20h
    ran-simulator-55dc5f56c6-fjc5k   1/1     Running   0          20h
  ```
Step 7. Verify  Handover request processing time with CMxApp and RAN simulator pod from 'smartedge-apps' namespace 

   Note: Minimum active UE number should be 50 and maximum number of UE 100. The total running time will be more than 4 hours and 99% the total Handover request processing time should be less than  0.1 to 0.15 seconds. 
         
  ```shell
    smartedge-open@ubuntu-4b70b7ba43:~$ kubectl logs cm-xapp-6d99d58b5-2l4t2 -n smartedge-apps -c cm-xapp
  ```
```shell
02/24/2022 11:00:40 AM Number of Cells: 7
02/24/2022 11:00:40 AM Queue len: 19
02/24/2022 11:00:40 AM Calling control req no 1 for UE : 2852134 Serving cell: 13842601454c001 target_cell 13842601454c002
02/24/2022 11:00:40 AM Number of Active UEs: 19
02/24/2022 11:00:40 AM Number of total UEs: 71
02/24/2022 11:00:40 AM HO processing time: 0.0503 seconds
02/24/2022 11:00:40 AM Queue len: 17
02/24/2022 11:00:40 AM Calling control req no 2 for UE : 3935705 Serving cell: 13842601454c004 target_cell 13842601454c003
02/24/2022 11:00:40 AM Number of Active UEs: 19
02/24/2022 11:00:40 AM Number of total UEs: 71
02/24/2022 11:00:40 AM HO processing time: 0.0445 seconds
02/24/2022 11:00:40 AM Queue len: 14
02/24/2022 11:00:41 AM Calling control req no 3 for UE : 5401234 Serving cell: 13842601454c005 target_cell 13842601454c006
02/24/2022 11:00:41 AM Number of Active UEs: 19
02/24/2022 11:00:41 AM Number of total UEs: 71
02/24/2022 11:00:41 AM HO processing time: 0.0521 seconds
02/24/2022 11:00:41 AM Queue len: 11
02/24/2022 11:00:41 AM Queue len: 10
02/24/2022 11:00:41 AM Calling control req no 4 for UE : 2164921 Serving cell: 13842601454c007 target_cell 13842601454c006
02/24/2022 11:00:41 AM Number of Active UEs: 19
02/24/2022 11:00:41 AM Number of total UEs: 71
02/24/2022 11:00:41 AM HO processing time: 0.0555 seconds
02/24/2022 11:00:41 AM Queue len: 8
02/24/2022 11:00:41 AM Queue len: 7
02/24/2022 11:00:41 AM Calling control req no 5 for UE : 5984583 Serving cell: 13842601454c001 target_cell 13842601454c002
02/24/2022 11:00:41 AM Number of Active UEs: 19
02/24/2022 11:00:41 AM Number of total UEs: 71
02/24/2022 11:00:41 AM HO processing time: 0.0633 seconds
02/24/2022 11:00:41 AM Queue len: 5
02/24/2022 11:00:41 AM Calling control req no 6 for UE : 7319340 Serving cell: 13842601454c006 target_cell 13842601454c001
02/24/2022 11:00:41 AM Number of Active UEs: 19
02/24/2022 11:00:41 AM Number of total UEs: 71
02/24/2022 11:00:41 AM HO processing time: 0.0354 seconds
02/24/2022 11:00:41 AM Queue len: 3
02/24/2022 11:00:41 AM Calling control req no 7 for UE : 3997593 Serving cell: 13842601454c004 target_cell 13842601454c003
02/24/2022 11:00:41 AM Number of Active UEs: 19
02/24/2022 11:00:41 AM Number of total UEs: 71
02/24/2022 11:00:41 AM HO processing time: 0.0352 seconds
02/24/2022 11:00:41 AM Queue len: 2
02/24/2022 11:00:41 AM Queue len: 1
02/24/2022 11:00:42 AM Queue len: 1
02/24/2022 11:00:42 AM Queue len: 1
02/24/2022 11:00:42 AM Queue len: 1
02/24/2022 11:00:42 AM Queue len: 1
02/24/2022 11:00:43 AM Queue len: 1
02/24/2022 11:00:43 AM Queue len: 1
02/24/2022 11:00:43 AM Queue len: 1
02/24/2022 11:00:43 AM Queue len: 1
02/24/2022 11:00:44 AM Queue len: 1
02/24/2022 11:00:45 AM Calling control req no 8 for UE : 1218889 Serving cell: 13842601454c001 target_cell 13842601454c002
02/24/2022 11:00:45 AM Number of Active UEs: 20
02/24/2022 11:00:45 AM Number of total UEs: 72
02/24/2022 11:00:45 AM HO processing time: 0.0467 seconds
```

Step 8. After latency measurement process, execute the following command to get xapp log
  
```shell
smartedge-open@esi101:/home/smartedge-open/Intelligent_Connection_Management$ kubectl -n smartedge-apps exec -it cm-xapp-6d99d58b5-2l4t2  -- bash
Defaulted container "cm-xapp" out of: cm-xapp, onos-proxy
openvino@cm-xapp-77d4995c8d-98mw7:~$ ls
HOprocess.py  __pycache__     cDQNandGNN.py  databaseProcess.py  oranHandOverEnv.py       queueManagement.py  xApp_ONF.py
OpenVINO      cActivation.py  csrc           onos_sdk_client.so  pygo_mediation_layer.py  weights.data        xapp.log
```
Step 9. Verify the xapp log file name using below command and dump logs as log.txt
      
```shell
smartedge-open@esi101:/home/smartedge-open/dek/tmp1$ kubectl cp smartedge-apps/cm-xapp-6d99d58b5-2l4t2:/home/openvino/xapp.log ./log.txt
Defaulted container "cm-xapp" out of: cm-xapp, onos-proxy
smartedge-open@esi101:/home/smartedge-open/dek/tmp1$ ls
log.txt
```
Step 10. Execute the following command from Python path

    Note: Minimum active UE number should be 50 and maximum number of UE 100 or 150. The total running time will be more than 4 hours and 99% the total Handover request processing time should be less than  0.1 to 0.15 seconds.
         Python file will store the numbers and when we run latest.py it will plot a graphs to verify Handover request processing time.

 ```shell
 smartedge-open@ubuntu-4b70b7ba43:/home/smartedge-open/dek/tmp1:$ python3 latest.py
 ```
 ![image](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/738863d7-a8b2-4b1c-b043-74daab6c789a)

Step 11. Validating the latency measurement
   
  Latency measurements are deduced based on Handover request processing time and the expectation is to be less than 0.1 second. Towards it the user has to check UE/Handover request and sort the Handover request processing time in csv format file. per the tabulated info a graph shall be plotted to verify Handover request processing time. 
  ![HOprocesstime](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/c8056fd7-fca0-44ba-a55f-1873fa6568a7)
  ![QueueSize](https://github.com/intel-innersource/applications.services.smart-edge-open.test-validation/assets/93578898/fee5b0d2-a475-485b-b2fc-22fc2b82edef)

