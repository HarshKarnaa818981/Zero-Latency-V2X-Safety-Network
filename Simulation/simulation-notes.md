**Zero-Latency V2X Safety Network — Interactive Mountain-Road Model**

This HTML model presents an interactive 3D simulation of vehicle coordination on mountainous roads with blind hairpin bends and wildlife crossings. The environment includes uphill and downhill traffic, five roadside processing units (RPUs), vehicle onboard units (OBUs), and a forest sensing location.

Users can compare **NORMAL mode**, which illustrates scripted hazards without coordination, with **V2X mode**, which demonstrates communication-assisted traffic management. Simulated vehicle information supports priority decisions, while visible commands tell vehicles when to proceed, wait, or slow down. Inspection panels display vehicle conditions, communication paths, priority reasons, and simulated OLED messages.

The model contains six selectable scenarios:

| Scenario | Demonstration |
|---|---|
| Emergency vehicle traffic | Priority coordination involving ambulances, police vehicles, and other traffic. |
| Different load conditions | A loaded uphill truck competing with opposing vehicles. |
| Equal heavy vehicles | Loaded trucks on both approaches, with arrival order resolving priority. |
| Normal traffic and lane discipline | Vehicles use their respective lanes without unnecessary exclusive priority. |
| Wildlife crossing | Simulated forest sensing produces warnings and controlled slowing or stopping. |
| Rainfall, landslide, and RPU failure | A lead vehicle clears Bend 03 before a landslide, then propagates warnings through simulated vehicle-to-vehicle communication. |

Interactive controls allow users to select scenarios, inspect road sections and system components, pause or replay movement, and enable environmental or warning sounds. The landslide demonstration also provides a clearance control to illustrate traffic recovery.

This model is an **illustrative software simulation** for explaining the project’s operation. Its vehicle movements, sensor values, communication links, and hazard outcomes do not establish measured hardware performance or real-world collision prevention.