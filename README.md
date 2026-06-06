# Reachfar V24 / V44 Notes
Results of my tests on Reachfar gps trackers V24 and V44

## Hardware

### Battery
### Solar Panel
### Charging Connector
### Waterproofing
### Mechanical Protection

## Protocol

### LK Messages

Official protocol example:

```text
[3G*2104346361*0008*LK,0,0,4]
```

Vendor explanation:

- Sent every 4–6 minutes.
- Maintains TCP long connection.
- Reports tracker IP/port to the server.

Observed behavior:

- Continues to be sent in power saving mode (`UPLOAD,65535#`).
- Allows the server to keep communicating with the tracker.
- Tracker remains reachable for remote commands.

Flespi observations:

- `message.type = LK`
- Battery level is reported.
- `steps.count` is reported.
- `turnover.number` is reported.

Example:

```json
{
  "message.type": "LK",
  "battery.level": 95,
  "steps.count": 0,
  "turnover.number": 0
}
```

Current interpretation:

- LK is not only a TCP keepalive packet.
- LK also contains basic device status information.

Unknown:

- Exact meaning of the parameters in:

```text
LK,0,0,4
```

- Whether additional status information is present in the raw packet.
### CR Command
### UPLOAD Command
### Alarm Messages
### TCP Connection

## Power Management

### Power Saving Mode
### Battery Behaviour
### Solar Charging
### LED Consumption

## Accelerometer

### Vibration Alarm
### Remove Alarm
### Motion Detection
### Open Questions

## Commands

### GPS Reporting
### LEDs
### Alarms
### Device Settings

## Flespi

### Device Setup
### Message Types
### Filters
### Remote Commands

## Home Assistant

### Integration
### REST Commands
### Automations
### Geofencing

## Experiments

### 2026-06

#### CR Behaviour
#### UPLOAD Intervals
#### LK Analysis
#### Power Saving Tests

## Findings

### Verified
### Probable
### Unknown

## Open Questions

## References

### Official Protocol
### Vendor Replies
### Community Findings
