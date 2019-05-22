- Cluster as a Device
- Dedupliation
- Exactly-once
- SAGA

# BO modification

- Partition Handler as Device
- 

# Device

- Device sends events in a sequence (DeviceLinkID + offset)
- DeviceLinkID `int32` refers to a link record {WorkspaceID int64, DeviceID int64}
- Log must not contain same offset from same device twice

# ??? Partition Handler as Device

- Event without device must be linked to Partition Handler
  - This number will be further used to sync logs with forked workspaces
  - By default workspace device number is 0
  - Forked workspaces have their own device number

# Dedupliation

- Can be `by-device-sequence` and `by-key`
- `by-device-sequence` is cheap deduplication, but events must be linked to a device id and sent in a sequence
- Per-key is expensive deduplication since every time key is checked

# Exactly-once
- 

# SAGA

- Event may require a Saga
- Event is stored to a temp persistent storage, offset is assigned
- Saga is played
- Event is copied to a log

Recovering
- When partition processor is started if must complete Saga from
