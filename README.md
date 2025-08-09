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
  
---
## Creating the Layout
The first step in the CMOS inverter layout design process is creating the transistor-level schematic. The schematic shown above has been implemented using the GPDK 90nm technology library in Cadence Virtuoso.
The circuit consists of:

- **PMOS transistor (PM0)*** : It is connected at the top, with its source tied to VDD and drain connected to the output node.<br>
- **NMOS transistor (NM0)*** : It is connected at the bottom, with its source tied to GND and drain connected to the output node.<br>
-Both transistor gates are shorted together to form the input node.<br>

***Key Parameters:***
- Channel length (L): 100 nm for both PMOS and NMOS.<br>
- Channel width (W): 120 nm for both devices.<br>
- Multiplication factor (m): 1 (single device per type).<br>

***Working Principle:***
When the input is logic high (1), the NMOS conducts and the PMOS is turned off, pulling the output to GND (logic low). When the input is logic low (0), the PMOS conducts and the NMOS is turned off, pulling the output to VDD (logic high). This complementary switching behavior provides low static power dissipation and rail-to-rail output swing.<br>
This schematic forms the functional base for the subsequent layout design, DRC (Design Rule Check), LVS (Layout Versus Schematic), and post-layout simulation stages. The layout will be created using the same technology parameters to ensure electrical equivalence between the schematic and physical design.Now following steps need to be followed fo layout design <br>


## Step 1: Launch Layout XL
In Virtuoso, go to the **top left corner** and click on: ***Launch-> Layout XL***
A start-up options window will appear.

---

## Step 2: Create New Layout
- Select **Create New** and click **OK**.

---

## Step 3: Verify New File Details
- A **New File** form appears.  
- Ensure that:
  - **Library**should be same as the schematic library.
  - **Cellname**should be same as the schematic cell name and **Viewname**
 By default it will load,user has to just check it.
- Click **OK**.

---

## Step 4: Layout and Schematic Windows
- The **LSW (Layer Select Window)** and a blank layout window appear along with the schematic window.
- The blank black area represents the **p-type substrate**.

---

## Step 5: Adding components to the Layout
Before adding  the component, displaying options should be aligned properly so that the MOSFET layout which is added will be clearly visible.<br>
On top goto ***Options-> Display Options***<br>
Adjust the display settings for better visibility:
 - **Grid Control**: Set `X Snap Spacing` = 0.005, `Y Snap Spacing` = 0.005  
 - **Display Levels**: Start = 0, Stop = 10  


---

## Step 6: Generate Layout from Schematic
Now for adding the components, goto **Connectivity**->**Generate**->**All from Source**.<br>
Now a window of Generate Layout will be opened as shown in Fig. 5.
In the **Generate Layout** window, check **I/O pins**, **PR boundary** and**Extract Connectivity after Generation.**
- Click **OK**.

---

## Step 7: Initial Layout View
- The layout (top view) of the respective MOSFETs appears according to the chosen technology, i.e., it will be predesigned.
- For the CMOS inverter:PMOS and NMOS layouts appear with **vdd**, **gnd**, **in**, and **out** markings.

---

## Step 8: Customize Layout Connections
- For moving the layouts, just after selecting the layout ,**press m**.
- For making  connections, Press **Ctrl + Shift + w**.
This will initialize line tool for drawing the metallic/ploy/required connection between the areas in layout. Appropriate Layers (Metal, polySi, etc) from the LSW can be selected
Note: Merging of same nets are also allowed. From **Create->Shape**,many options for other shapes are available for drawing.

---

## Step 9: Add N-Well Region for VDD
- PMOS requires an **N-well** as it is made on an N-type substrate.
  For this **select WN from LSW** and then, **rectangle shape** can be selected by **pressing R** or from **Create->Shape->Rectangle**. Now draw the N well region as required.

---

## Step 10: Create N-Well and P-Well Tapping
-  Now for the exact connection of VDD,**N Well tapping** on the created NWell region is made. This is done by clicking on **Create -> Multipart path** and then **press F3**.
- From the Multipart path window appearing, in **MPP template** select **NWELL Tap** and click **Hide**. Go to the earlier created N Well region and just click once, and drag to draw
 the NWell tapping.
- Similar to this for **ground connections, PWELL tapping** can be directly selected from the **Multipart path** and drawn on the P type substrate (which is the black area).
  
---

## Step 11: Connect Gates with PolySi and Vias
- The polySi ( i.e., the gate) of both the NMOS and PMOS are connected together for inverter input. Now to provide the contact vias for the polySi and metal1 again click on **Create-> Multipart Path** and then **press F3**. In MPP template, select **GC_M1** andclick hide. Now just draw on the polySi gate input

---

## Step 12: Label Ports
- Labels for **in**, **out**, **vdd**, and **gnd** must match schematic names.
- Press **`L`** to label.
-  Give the names of the ports as in schematic in the Label (Pattern). Select Layer as **M1 Label**. Now Click on Hide and start placing the labels at respective positions.
---

## Step 13: Save the Layout
- Once all connections and labels are complete, save the design.
- Ensure the layout matches the schematic in connectivity before moving to DRC/LVS.

---




