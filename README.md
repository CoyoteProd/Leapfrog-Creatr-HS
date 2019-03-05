# Leapfrog-Creatr-HS

Latest Marlin firmware for Leapfrog Creatr Hs based on Marlin 1.1.9

100% Compatible with the original mainboard

### WARNING ! 	
These releases seems to break communication with the display (Olimex A20). 

( Probably because by defaut Creatr HS use Checksumed Protocol ? )
### WARNING ! 	

## Marlin Std:
 - Acceleration and Feedrate diminued to have correct Print.
 - Linear Advance activated with Coef : 1.00

## Marlin BLTouch (same Standard settings)
- Add BLTouch

![alt text](Marlin%20BLTouch/Pict/BLTouch.jpg "BLTouch img")
 
 - Connect Z (Black/White) on Zmin connector
 - Connect SERVO0_PIN on 52 (SCK) (physical pin 20 of ATMega2560) (see picture)

Once installed, use this sequence to determine if the BLTouch is setup properly :

Connect BLTouch, power up controller and upload the firmware

Blue LED will be ON if a servo signal is present. Blue LED is faint.

M119		; should return OPEN. If not check that the BLTouch is enabled in the configuration. If enabled then check wiring and check that the correct pin is being used. Also check that Z_MIN_ENDSTOP_INVERTING and Z_MIN_PROBE_ENDSTOP_INVERTING are both set to "false".

M280 P0 S10 	; should deploy the probe and the orange LED will be OFF.

M119 		; should return OPEN

M280 P0 S90 	; should stow the probe and the orange LED will be ON

M280 P0 S60 	; puts it into the M119 test mode.
		; The probe should remain stowed and the blue LED should be OFF. If it's ON then the unit needs to be adjusted.

M119 		; should return TRIGGERED

M280 P0 S160 	; returns it to normal operation

M119 		; should return OPEN.

After that, Lower the bed to max, and initiate a Z Home (G28 Z) with a finger on the power supply (Safety first)
During Homing with other finger trigg bltouch: the bed must stop...( if not poweroff before crash....)

			
Future update : 
 
 - New Display interface for Olimex A20
 - (Add 200v Heated Bed with SSR)
 - (Change Nozzles by Volcano E3D)
 
Forked from : https://github.com/ledfreak3d/Leapfrog-Creatr-HS-New-Firmware

Original Firmware : https://github.com/Leapfrog3DPrinters/CreatrHS_Firmware_2.5
