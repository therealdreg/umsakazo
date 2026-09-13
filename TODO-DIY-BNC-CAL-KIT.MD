## TO-DO: Cheap DUTs to compare DIY BNC calibration vs SMA calibration kit

Goal: check whether the DIY BNC calibration kit gives practical amateur-level results close to a reference SMA calibration kit.

### Test rules

- [ ] Use the same NanoVNA, sweep range, number of points, adapters, and settings
- [ ] Save screenshots for both calibrations
- [ ] Compare both traces and marker values
- [ ] Repeat each DUT connection at least 3 times

### DUTs to test

- [ ] **Independent 50 ohm load**  
  Check whether both calibrations show a similar match, return loss, and impedance

- [ ] **Fixed attenuator (3 dB / 6 dB / 10 dB)**  
  Check S21 attenuation and overall flatness

- [ ] **Short coax cable**  
  Measure with open and short at the far end, then compare Smith chart behavior

- [ ] **BNC barrel / SMA-BNC adapter / through adapter**  
  Check insertion loss and mismatch

- [ ] **Simple resistive DUTs (33 ohm / 75 ohm / 100 ohm)**  
  Check whether the measured mismatch and impedance make sense

- [ ] **Cheap LC or SAW filter**  
  Compare passband, stopband, and general trace shape

- [ ] **Optional real-world DUT**  
  Small antenna, matching network, or radio dummy load

### Suggested test order

- [ ] 50 ohm load
- [ ] Fixed attenuator
- [ ] Short coax cable
- [ ] Adapters / barrel
- [ ] 33 ohm / 75 ohm / 100 ohm loads
- [ ] Filter
- [ ] Optional antenna-related DUT

### Practical pass/fail criteria

- [ ] **PASS:** results are close to the SMA calibration kit across the intended frequency range
- [ ] **PASS:** repeated connections give similar results
- [ ] **PASS:** loads, attenuators, cables, and filters behave as expected

- [ ] **WARNING:** noticeable differences appear only near the upper frequency limit

- [ ] **FAIL:** results change too much after reconnecting the DUT
- [ ] **FAIL:** DUT behavior looks clearly wrong compared to the SMA calibration kit
- [ ] **FAIL:** the DIY kit only looks good when measuring its own standards
