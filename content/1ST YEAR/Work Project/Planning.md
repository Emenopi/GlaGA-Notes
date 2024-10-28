
SPIKE: INVESTIGATE WHICH DATA CAN BE USED, WHICH ENDPOINTS EXIST, AND WHICH ENDPOINTS REQUIRE IMPLEMENTATION

- Animation:
- API integration:
- Data selection inputs:
- UI: "Visualise On Map" button

VERSION ZERO: GLOBAL POWER SUPPLY OVER 10Y: electric v2g
---
Data required: power supply (GWh) per country
UI: setPitch(number) (IN SAME FILE AS SETZOOM())

AS A: Lens power user
WHEN: I click "visualise on map"
THEN: The map will tilt forward and selected data will be visualised on z-axis as animation

GIVEN: I have clicked "visualise on map"
WHEN: The map visualisation loads
THEN: All previously applied layers will be hidden
AND: Only the visualisation animation will show

GIVEN: I am viewing map data visualisation animation
WHEN: I exit this mode
THEN: Previously applied layers will be restored
AND: visualisation animation will disappear