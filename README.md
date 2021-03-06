# indi-wheel
   An Arduino Nano stepper driven Indi compatible DIY filter wheel for remote astronomy/AP 

By: Ray Wells

CC: Markku Siitonen who provided the skeleton and protocol code. 

  This motorized remote filter wheel uses an Arduino Nano with a 24byj-48 gearhead stepper motor and the uln2003 driver board that comes with it.  It is powered by 5v from the usb port in bipolar configuration.

Hardware
A generic 5 position manual filter wheel with the stepper's double flat shaft epoxied into the wheel center screw hole (after removing the screw of course).
I used header pins to connect the driver board directly to the nano to reduce wiring mess and a single hall effect(HET) that came with an on board comparator(for a digital output) powered by nano i/o for simplicity. To get around the calibration errors that sometimes creep into these systems, I set it so it would only move one way to prevent backlash. It also resets to the home position(HET) whenever it would normally move backward and then moves forward from 0 to the new filter position. Some amount of experimentation is currently needed to get the initial step calibration for each position in the array.

Indi compatability
USB Protocol emulates the Xagyl filter wheel in order to communicate with the existing Indi/Ekos driver.
Due to design restrictions, some buttons do nothing in the indi control panel but indexing works for all 5 positions.

Todo: arrange the serial offsets so they can be used to fine tune position. This will likely be a converter where 0-100 becomes -50 to +50. 

Known bugs. Due to my position of the HET, moving from filter5 to filter1 results in a position error due to the HET being already on the magnet. ---edit: I fixed this by having it back up a bit to get off the het and retry the home. The only time it runs reverse.
