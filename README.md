# OP70 Palletizing Cell

This project provides the functional description for  for Operation 70 (OP70), a key part of Line 4 at Advance Motors AB. The system is designed to handle products and pallets efficiently within an automated manufacturing process. It uses a series of conveyors, a robotic pick-and-place station, and various safety features to sort and manage workpieces, particularly those that have been rejected.

## This repository

You can find the doc about the ... here:

PLC programming:

Final presentation:

Design using 

HMI design:

## Key Features

Conveyor Systems: The system includes eight conveyors for workpieces and two larger belt conveyors for pallets. Each conveyor has sensors to detect items and is powered by a double motor contactor, allowing movement in both directions.

Robotic Station: An IRB 6640 robot with a magnetic gripper is used to move rejected workpieces. The robot picks up the pieces from the main conveyor line and places them onto pallets on the reject conveyor line.

Pallet Handling: The system includes a pallet dispenser that can hold a maximum of 10 pallets. It's designed to ensure that empty pallets are always available for rejected products.

Safety Measures: The operation is enclosed by 2.5-meter-high fences. It features multiple safety gates (SOP740-SOP742) and light curtains (SOP743-SOP744) that provide safe access for forklift operators and maintenance personnel. These safety devices are managed by an HMI (Human-Machine Interface).

Data and Signals: The system uses a binary interlock protocol for safe product transfer. Production data, including 'Product Number', 'ID Number', and 'Status', is transferred between operations.


## System Overview
The project is structured into several sub-operations:

SOP700: Main cabinet housing the control PLC, power supplies, and other essential devices.

SOP710-SOP717: The primary conveyors for the flow of products.

SOP720-SOP722: The conveyors responsible for the flow of pallets.

SOP730: The dedicated pick-and-place station for the robot.

SOP760: The pallet dispenser.

## Workflow
Product Transfer and Rejection
A product from the previous operation (OP60) is received by OP70. The product moves along the main conveyor until it reaches SOP712. The system checks the product's 'Status'. If the product is "rejected," a physical stopper is activated, preventing it from continuing down the main line. The robot picks up the rejected piece and places it on a pallet.

## Pallet Handling
A sensor on the conveyor checks if a pallet is needed for rejected workpieces. If the ReadyToDispense signal is active, the pallet dispenser places a new pallet. The pallet moves to the placement area and is held in place by a physical stopper. A Refill signal activates when the pallet stock drops below three, alerting the forklift operator.
Once a pallet is full or the batch type changes, it is sent to the final conveyor (SOP722) for extraction.
