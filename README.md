# CMOS Inverter Layout Design using Cadence Virtuoso

This project showcases the complete custom design flow of a **CMOS Inverter**, implemented using **Cadence Virtuoso** with the **GPDK 90nm** technology. It covers various guiding steps which will help in understanding the design process in creating a custom IC layout for the CMOS design. Once the designing of the layout is done using the Virtuoso Layout XL, one can move onto the ***Design Rule Check (DRC)***,  and then to ***Layout V/s Schematic (LVS)***. 
In VLSI design, as processes become more and more complex, need for the designer to understand the intricacies of the fabrication process and interpret the relations between the different photo masks is really troublesome. Therefore, a set of layout rules, also called ***design rules***, has been defined. They act as an interface or communication link between the circuit designer and the process engineer during the
manufacturing phase . Before moving onto the layout editing, inverter schematic circuit diagram should be made in the Cadence Virtuoso tool. The newly created CMOS inverter design  should be functionally verified. A schematic which is not functionally correct will yield a layout that is also  incorrect. 
 Once the physical layout of a circuit is created, it is crucial to ensure that this layout accurately represents the original schematic. This verification is performed through a process called ***Layout vs Schematic (LVS)***. LVS compares the netlist extracted from the layout against the netlist from the schematic and verifies whether both describe the same circuit. This check ensures that no errors have been introduced during layout creation such as incorrect transistor sizes,  mislabeled pins or missing connections. The layout must have the same number of devices, correct connectivity, and matching port names as the schematic. If the LVS fails, the designer must carefully re-examine the layout and correct any discrepancies. Only after a successful LVS match the design can be considered ready for further verification stages like parasitic extraction.



---

##  Tools & Technology

- **Cadence Virtuoso 6.1.7-64b** – Schematic and layout design  
- **Calibre v2016.1_14.11** – Physical verification (DRC, LVS)  
- **GPDK 90nm** – Process Design Kit used
- 
---

