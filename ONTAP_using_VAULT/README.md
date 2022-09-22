### Usage Example
## Run the program


1. Creating a snapshot

```bash
snapshot_ops_vault.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --create
```

2. Remove a snapshot
```bash
snapshot_ops_vault.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --remove
```

3. GET a list of all snapshots
```bash
snapshot_ops_vault.py -s <STORAGE> -vm <SVM> -vn <VOLUME_NAME> --list
```
    		

4. HELP
```
snapshot_ops_vault.py -h | --help
```

5. VERSION
```
snapshot_ops_vault.py --version
```

- [STORAGE] => name of your storage
- [STORAGE VM] => name of your SVM
- [VOLUME NAME] => name of the Volume