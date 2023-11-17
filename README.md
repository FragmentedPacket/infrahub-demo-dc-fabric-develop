# infrahub-demo-dc-fabric

![infrahub-demo-dc-fabric drawing](./infrahub-demo-dc-fabric.excalidraw.svg)

## Playbook

### 1. Log into UI
### 2. Show schema extensibility
```shell
infrahubctl schema load models/infrastructure_topology.yml
```
### 3. Load in topology data only
```shell
infrahubctl run models/infrastructure_topology.py
```
### 4. Paste API key
```graphql
mutation {
  CoreRepositoryCreate(
    data: {
      name: { value: "naf-demo" }
      location: { value: "https://github.com/fooelisa/infrahub-demo-dc-fabric.git" }
      username: { value: "fooelisa" }
      password: { value: "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" }
    }
  ) {
    ok
    object {
      id
    }
  }
}
```

### 5. Load in first pod of devices
```shell
infrahubctl run models/infrastructure_devices.py
```
### 6. Rfiles
```shell
infrahubctl render device_startup device=atl-spine1
```
### 7. Show a proposed change
  - All checks here should pass
### 8. Show a check
  - Delete a device via the UI
  - Create a PC
  - Check should fail now
### 9. Load in second pod of devices
```shell
infrahubctl run models/infrastructure_devices_2.py
```