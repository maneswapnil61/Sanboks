SANBOKS - Simulation and Numerical Benchmarking of Kinetic System

Created by - Swapnil Mane, Yash Bhat, Malhardutt Hublikar, Dhanashree Khairnar, Tirth Raval.

Contact details - maneswapnil61@gmail.com, yashrbhat@outlook.com (9326019863), mahublikar99@gmail.com


**SANBOKS is an open source MATLAB/Simulink program developed to simulate an RWD EV. 
**It is a quasi-static simulation of a point mass vehicle model with a g-g-v performance envelope.
**Remember, garbage input equals garbage output. Your simulation output is only as good as the input that it is fed. 
**The values of mass, weight distribution, rolling resistance coefficient, tire friction coefficients, the lift and drag coefficients, the aero balance that we have used are educated guesses that are to be experimentally verified.
**Remember to add proper file path for the input spreadsheet at the top of the script, and the SIMULINK model at the bottom of the script.
**Note that running the F1 setup spreadsheets requires the addition of max_speed="value in m/s"; on line 66 of Sanboks_V0_3 script. 	


**Potential Improvements  - Longitudinal load transfer can technically be addeded into our program by adding the load transfer into the normal force, even though it is a point mass model. This should significantly affect program accuracy.
			  - Motor efficiency maps are available for Saietta/Agni and Emrax motors. Integrating motor efficiency map data into the program will increase output accuracy.
			  - Move away from a point mass model ASAP. It doesn't take into account load transfer and tire slip. It can't calculate yaw moment for torque vectoring purposes.
			  - A single-track model (bicycle model) or a two-track model with complete suspension model (springs, dampers and everything) can be used to estimate roll, pitch and yaw.
 			  - The Pacejka tire model can be included in the future for Hoosier slicks (Tire Testing Consortium [TTC] data) or MRF slicks (Used by Raftaar Racing).
			  - Modeling transient effects such as temperature affected performance. This will be a massive effort and will probably not have a significant impact on result accuracy.


Spreadsheet Input data -

1. Mass 				- Vehicle Mass 							-(in kg).
2. Eq. Rotational Mass 			- Equivalent mass of rotational components of drivetrain 	-(in kg).
3. Rear weight distribution 		- % weight on the rear axle 					-(inputs from 0 to 1)
4. Number of laps			- Total number of laps 						-(default set to 17 as we have autocross track instead of endurance).

5. Tire Radius 				- Tire Rolling Radius						-(in meters)
6. Coefficient of Rolling Resistance 	- Rolling Resistance coefficient   				-(default 0.015. Values vary with tire pressure. Obtainable through coast down test.)
7. Longitudinal Friction 		- Coefficient of friction of tire and road (longitudinal) 	-(default 0.9. Unsure about actual value)
8. Lateral Friction 			- Coefficient of friction of tire and road (lateral) 		-(default 1.0. Unsure about actual value)

9. Number of motors			- Total motors in the vehicle 					-(For Agni 119R, 2)
10. Time for peak torque 		- Number of seconds motor can sustain peak operation 		-(For Agni 119R, 5 seconds max, 3 seconds is recommended by manufacturer.)
11. Final Gear Ratio 			- Overall gear ratio 						-(One of the variables that is to be optimized through SANBOKS)
12. Final Power Efficiency 		- Efficiency of the drivetrain and motor multiplied		-(inputs from 0 to 1)
13. Supply Voltage 			- Supply voltage for a SINGLE MOTOR 				-(in Volts)

14. Frontal Area 			- Vehicle frontal area (body and tires frontview area) 		-(in m^2)
15. Lift Coefficient 			- Vehicle Lift coefficient ()					-(we used 2x drag coefficient)
16. Drag Coefficient			- Vehicle Drag coefficient ()					-(default 0.35. Unsure about actual value. Obtainable through coast down test.)
17. Aero balance 			- % downforce acting on the rear 				-(inputs from 0 to 1)

18. Front braking torque 		- Front axle braking torque 					-(in N-m)
19. Rear braking torque 		- Rear axle braking torque 					-(in N-m)

20. Minimum Track radius 		- Minimum track radius for track as defined in rules 		-(in meters. 4.5, as per FB2021 updated rulebook)
21. Steering Ratio 			- Steering ratio for lateral acceleration O/P in Simulink 	-()

22. Motor Data 				- Motor Data, peak O/P on the left, continuous on the right. 	-(No Load Current drawn for Agni 119R is 7A at 72V. Do not change it to 0.)	
23. Coordinates 			- x and y coordinates of track. 				-(in mm. Z is ignored. We can collect track data by logging coordinates on an actual run).



Inspired by - Honorable Principal Dr. Sanjay Bokade.
		- The main reason behind making this simulation was the tale of the 2010 Formula Student Italy competition told to us by none other than Bokade sir.
		- The car taken to that event was in his words "oversafe", which was ultimately the reason for their failure to participate in the dynamic events.
		- Ten years since then, the team has not yet participated in a single dynamic event.
		- The intention was to make a vehicle development tool for our electric vehicle in the 2022 season, to ensure that TR Racing shall never know such shame again.






















"FSAE is your interest, the college doesn't need it. You should give something to the college; the college owes you nothing." __ Dr. Sanjay Bokade.
"Here you go, take this." __ Mane.			# Sanboks
