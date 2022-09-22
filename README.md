# Netapp_snapshot
This repository contains sample scripts illustrating how to use the ONTAP(NETAPP) REST API. This repository also contains a script that shows how to use Vault on ONTAP(NETAPP) REST API

# snapshot_ops

This repo contains simple program that `CREATE`, `LIST`, and `REMOVE`  NETAPP snapshots in a specific ONTAP/NETAPP storage.


### Features
- `CREATE` a snapshot
- `REMOVE` a snapshot
- Get the `LIST` of Snapshots
- Helpful CLI

### Requirements
- Python 3.6 or higher
- requests 2.21.0 or later
- ONTAP 9 (NetApp storage system) or higher (untested on earlier versions)
- Install docopt

Check [install docopt](https://pypi.org/project/docopt/) for more information

- Install PrettyTable

Check [install prettytable](https://pypi.org/project/prettytable/) for more information


### Usage Example
## Run the program


1. Creating a snapshot

```bash
snapshot_ops.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --create
```

2. Remove a snapshot
```bash
snapshot_ops.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --remove
```

3. GET a list of all snapshots
```bash
snapshot_ops.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --list
```
    		

4. HELP
```
snapshot_ops.py -h | --help
```

5. VERSION
```
snapshot_ops.py --version
```

- [STORAGE] => name of your storage
- [STORAGE VM] => name of your SVM
- [VOLUME NAME] => name of the Volume


## Release Instructions
1. Update `CHANGELOG.md` with new version



```mermaid
flowchart TB
    S([START]) --> IO[/INPUT<br>Storage<br>StorageVM<br>Volume Name<br>Operation:<br><i>CREATE,REMOVE,LIST/]
    IO --> CR[CREATE]
    CR --> ID[Get Volume UUID]
    ID --> VOL{If Volume exist}
    VOL --NO--> NVOL>Volume does not exist]
    NVOL ----> STP[END]
    VOL --YES--> SN[/Get Snapshot name/]
    SN --> CRT{CREATE snapshot}
    CRT --SUCCESS--> DSP3{Check Job state}
    DSP3 --ERROR--> DSP4>Display ERROR]
    DSP3 --SUCCESS--> DSP5>Display: <br>State<br>Details]
    DSP5 ----> STP
    CRT --ERROR--> TT>Display Error]
    TT ----> STP
    IO --> LS[LIST]
    LS --> ID
    ID --> VOL
    VOL --NO--> NVOL
    NVOL ---> STP
    VOL --YES--> SP{GET all Snapshots<br> from the Volume given}
    SP --ERROR--> ERR1>Display the ERROR]
    ERR1 ---> STP
    SP --SUCCESS--> SUCC1>Display All Snapshots<br>UUID and NAME]
    SUCC1 ---> STP
    IO --> RM[REMOVE]
    RM --> ID
    ID --> VOL
    VOL --NO--> NVOL
    NVOL --> STP
    VOL --YES--> SN
    SN --> SPID[Get snapshot UUID]
    SPID --> CSP{Check if Snapshot Exist}
    CSP --NO--> SPN>Snapshot not found]
    SPN --> STP
    CSP --YES--> SPN1{Snapshot not found}
    SPN1 --FAILED--> DPS2>Display Error]
    DPS2 --> STP
    SPN1 --SUCCESS--> DSP3{Check Job state}
    DSP3 --ERROR--> DSP4>Display ERROR]
    DSP4 --> STP
    DSP3 --SUCCESS--> DSP5>Display: <br>State<br>Details]
    DSP5 --> STP 





style CR stroke:green,stroke-width:1px
style LS stroke:blue,stroke-width:1px
style RM stroke:red,stroke-width:1px



linkStyle 1 stroke-width:2px,fill:none,stroke:green;
linkStyle 2 stroke-width:2px,fill:none,stroke:green;
linkStyle 3 stroke-width:2px,fill:none,stroke:green;
linkStyle 4 stroke-width:2px,fill:none,stroke:green;
linkStyle 5 stroke-width:2px,fill:none,stroke:green;
linkStyle 6 stroke-width:2px,fill:none,stroke:green;
linkStyle 7 stroke-width:2px,fill:none,stroke:green;
linkStyle 8 stroke-width:2px,fill:none,stroke:green;
linkStyle 9 stroke-width:2px,fill:none,stroke:green;
linkStyle 10 stroke-width:2px,fill:none,stroke:green;
linkStyle 11 stroke-width:2px,fill:none,stroke:green;
linkStyle 12 stroke-width:2px,fill:none,stroke:green;
linkStyle 13 stroke-width:2px,fill:none,stroke:green;





linkStyle 14 stroke-width:2px,fill:none,stroke:blue;
linkStyle 15 stroke-width:2px,fill:none,stroke:blue;
linkStyle 16 stroke-width:2px,fill:none,stroke:blue;
linkStyle 17 stroke-width:2px,fill:none,stroke:blue;
linkStyle 18 stroke-width:2px,fill:none,stroke:blue;
linkStyle 19 stroke-width:2px,fill:none,stroke:blue;
linkStyle 20 stroke-width:2px,fill:none,stroke:blue;
linkStyle 21 stroke-width:2px,fill:none,stroke:blue;
linkStyle 22 stroke-width:2px,fill:none,stroke:blue;
linkStyle 23 stroke-width:2px,fill:none,stroke:blue;



linkStyle 24 stroke-width:2px,fill:none,stroke:red;
linkStyle 25 stroke-width:2px,fill:none,stroke:red;
linkStyle 26 stroke-width:2px,fill:none,stroke:red;
linkStyle 27 stroke-width:2px,fill:none,stroke:red;
linkStyle 28 stroke-width:2px,fill:none,stroke:red;
linkStyle 29 stroke-width:2px,fill:none,stroke:red;
linkStyle 30 stroke-width:2px,fill:none,stroke:red;
linkStyle 31 stroke-width:2px,fill:none,stroke:red;
linkStyle 32 stroke-width:2px,fill:none,stroke:red;
linkStyle 33 stroke-width:2px,fill:none,stroke:red;
linkStyle 34 stroke-width:2px,fill:none,stroke:red;
linkStyle 35 stroke-width:2px,fill:none,stroke:red;
linkStyle 36 stroke-width:2px,fill:none,stroke:red;
linkStyle 37 stroke-width:2px,fill:none,stroke:red;
linkStyle 38 stroke-width:2px,fill:none,stroke:red;
linkStyle 39 stroke-width:2px,fill:none,stroke:red;
linkStyle 40 stroke-width:2px,fill:none,stroke:red;
linkStyle 41 stroke-width:2px,fill:none,stroke:red;


```

## Support

Report any issues to: https://github.com/DMarkStorage/Netapp_snapshot/issues. For any questions or concerns and send us an [email](daminimark@gmail.com)

To learn more about ONTAP REST APIs, visit https://devnet.netapp.com/restapi.php 