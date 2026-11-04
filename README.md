# Dell Inspiron 3585 — NVMe Copper Thermal Bridge

A reversible passive thermal-spreading modification for the NVMe SSD in a Dell Inspiron 3585.

**Project status:** documented real-world experiment. Results are observational, not a controlled laboratory benchmark.

[Polska wersja dokumentacji](README_PL.md)

## Overview

This project documents a simple copper thermal bridge fitted over the factory-labeled NVMe SSD. The copper plate provides an additional path for spreading heat toward the laptop's bottom cover.

The modification was designed to be reversible: no adhesive, thermal glue, drilling, or permanent change to the laptop was used.

## Hardware and materials

- Laptop: Dell Inspiron 3585
- SSD: SK hynix BC501, 512 GB (model HFM512GDJTNG-8310A)
- Copper plate: 20 × 65 × 0.5 mm
- Thermal interface: Arctic MX-2 thermal paste

## Construction

1. The copper plate is placed over the SSD's factory label.
2. Arctic MX-2 thermal paste is used at the SSD-label-to-copper interface.
3. The opposite side of the copper plate is pressed toward the laptop's bottom cover when the cover is fitted.
4. No adhesive or permanent mechanical modification is used.

The exact contact pressure and thermal resistance were not measured. The arrangement relies on the fit of the original laptop enclosure.

## Thermal observations

### Short comparative tests

Short before/after comparative tests indicated an approximately **14°C difference at NVMe temperature sensor 2** in favour of the copper-bridge configuration. These were short observations; exact absolute readings and a fully standardized test protocol are not available here. Sensor labels can differ between monitoring tools, so sensor numbering should not be assumed to map directly between HWiNFO, SMART, and Linux hwmon.

### Real-world video playback

A separate practical comparison was recorded during 1080p YouTube/VOD playback on the same external 28-inch monitor:

| Configuration | Observation period | Recorded maximum SSD temperature |
|---|---:|---:|
| Before the modification | Reached within 15 minutes | 69.8°C |
| After the modification | More than 7 hours of continuous playback | 57.9°C |

The difference between the two recorded maxima is **11.9°C (approximately 12°C)**.

Both sessions took place in the same room under ordinary ambient conditions, without deliberate additional ventilation or room cooling. The playback resolution and external monitor were the same.

**Important limitation:** the observation periods were not identical and this was not a laboratory-controlled test with a fully matched workload, fixed starting temperature, and continuous synchronized logging. The comparison is therefore presented as a practical real-world observation, not proof of a universal temperature reduction under every workload.

### Additional post-modification monitoring

Point-in-time Linux hwmon readings were collected on 1–3 November 2026. Across the ten recorded snapshots:

- NVMe temp1/temp2 readings ranged from 46.9°C to 52.9°C.
- NVMe temp3 readings ranged from 52.9°C to 58.9°C.
- temp3 was consistently about 6°C higher than temp1/temp2.

These are separate snapshots, not a continuous seven-hour temperature trace. The mapping between Linux hwmon sensor indices and the SSD's SMART sensor labels has not been independently verified.

### Baseline drive health

A pre-modification SMART report dated 31 October 2026 showed:

- Overall health: PASSED
- Critical Warning: 0
- Percentage Used: 1%
- Media and Data Integrity Errors: 0
- Error Information Log Entries: 0

This is a drive-health baseline, not evidence of the thermal bridge's effectiveness. The SSD serial number is intentionally omitted.

## Interpretation

The observations are consistent with the copper plate acting as a passive heat spreader in this particular laptop configuration. The strongest practical observation is that the recorded maximum during the longer post-modification video session was lower than the temperature reached during the shorter pre-modification session.

The data do not establish the exact heat-transfer path, the contribution of each contact surface, or performance under every possible workload and ambient condition.

## Safety and limitations

- Work on a laptop only when it is powered off and disconnected from external power.
- Avoid short circuits and prevent the copper plate from contacting exposed electrical components.
- Ensure the bottom cover closes normally and is not forced against the SSD or other components.
- Check that the plate does not interfere with the battery, cables, or other parts.
- Thermal paste is used as a contact interface; it is not a structural adhesive.
- The author assumes no responsibility for damage resulting from reproducing this modification.
- Laptop revisions and SSD layouts may differ. Inspect the exact device before attempting a similar modification.

## Repository contents

Project photographs and additional measurement records are intended to be organized under `images/` and supporting documentation as they are added.

## Credits

Physical modification, hardware work, and measurements: repository owner.

This repository records one device-specific experiment. It should not be treated as an official Dell service procedure or a guaranteed upgrade.
