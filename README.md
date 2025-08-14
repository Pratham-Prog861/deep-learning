Q.1 Fan Speed Control :-
  1. Inputs
  Temperature (0–50 °C)
  Low: Triangular MF → [0 0 25]
  Medium: Triangular MF → [15 25 35]
  High: Triangular MF → [30 50 50]

  Humidity (0–100 %)

  Dry: Triangular MF → [0 0 50]
  Normal: Triangular MF → [30 50 70]
  Humid: Triangular MF → [60 100 100]

  2. Output
  Fan Speed (0–10)
  Slow: Triangular MF → [0 0 5]
  Medium: Triangular MF → [3 5 7]
  Fast: Triangular MF → [5 10 10]

  3. Rules in MATLAB
  If Temp is High AND Humid is Humid → Fan Speed is Fast
  If Temp is Medium AND Humid is Normal → Fan Speed is Medium
  If Temp is Low AND Humid is Dry → Fan Speed is Slow


Q2. FLC in Simulink for Water Tank Level Control

  Inputs:
  Error (Desired – Actual Level): range [-10, 10]
  Negative → [ -10 -10 0 ]
  Zero → [ -5 0 5 ]
  Positive → [ 0 10 10 ]

  Change in Error: range [-5, 5]

  Negative → [ -5 -5 0 ]
  Zero → [ -2.5 0 2.5 ]
  Positive → [ 0 5 5 ]

  Output: Valve Control % (0–100)
  Close → [0 0 50]
  Medium → [25 50 75]
  Open → [50 100 100]

  Rules:
  If Error is Negative → Valve Open
  If Error is Zero → Valve Medium
  If Error is Positive → Valve Close


Q3. Room Heating Controller

  Inputs: (Trapezoidal MFs)
  Room Temp (0–40)
  Cold → [0 0 10 20]
  Normal → [15 20 25 30]
  Warm → [25 35 40 40]
  
  Outside Temp (0–40)
  Cold → [0 0 20 25]
  Warm → [20 30 40 40]

  Output: Heater Power (0–100)
  Low → [0 0 50]
  Medium → [25 50 75]
  High → [50 100 100]

  Rules:
  Room Cold AND Outside Cold → Heater High
  Room Warm → Heater Low
  Room Normal → Heater Medium


Q4. Fan Speed Control with Scope in Simulink

  Same as Q1 (Temperature vs. Humidity → Fan Speed).
  Load the FIS file into the Fuzzy Logic Controller block in Simulink:

  Input: Constant (temperature, humidity values) → FLC → Scope.

  Use same triangular MF numbers as Q1.

Q5. Smart Lighting System

  Inputs:

  Ambient Light (0–100)
  Dark → [0 0 50]
  Normal → [25 50 75]
  Bright → [50 100 100]

  User Preference (0–100)
  Low → [0 0 50]
  Medium → [25 50 75]
  High → [50 100 100]

  Output: LED Brightness (0–100)
  Dim → [0 0 50]
  Moderate → [25 50 75]
  Bright → [50 100 100]

  Rules:
  Ambient Dark AND Preference High → Brightness High
  Ambient Bright → Brightness Low
  Ambient Normal AND Preference Medium → Brightness Moderate

Q6. Braking System in Vehicles

  Inputs:
  Speed (0–120)
  
  Slow → [0 0 60]
  Medium → [40 60 80]
  Fast → [60 120 120]

  Distance to Object (0–100)
  
  Near → [0 0 50]
  Moderate → [25 50 75]
  Far → [50 100 100]

  Output: Brake Force (0–1)

  None → [0 0 0.5]
  Medium → [0.25 0.5 0.75]
  Full → [0.5 1 1]

  Rules:
  Speed Fast AND Distance Near → Brake Full
  Speed Slow AND Distance Far → Brake None
  Speed Medium AND Distance Moderate → Brake Medium


Q7. Washing Machine Time Control

  Inputs (Gaussian MFs):
  Dirt Level (0–10)
  Low → gaussmf(x,[1 0])
  Medium → gaussmf(x,[1.5 5])
  High → gaussmf(x,[1 10])

  Load Weight (0–10)
  Light → gaussmf(x,[1 0])
  Normal → gaussmf(x,[1.5 5])
  Heavy → gaussmf(x,[1 10])

  Output: Wash Time (10–60 min)
  Short → gaussmf(x,[5 10])
  Medium → gaussmf(x,[5 30])
  Long → gaussmf(x,[5 60])

  Rules:
  High Dirt & Heavy Load → Long Time
  Low Dirt & Light Load → Short Time
  Medium Dirt & Normal Load → Medium Time


Q8. Voltage Control in Power System

  Inputs:
  Load Demand (0–100%) → Low [0 0 50], Medium [25 50 75], High [50 100 100]
  Voltage Drop (0–10V) → Low [0 0 5], High [5 10 10]

  Output: Regulator Adjustment (%)
  No Regulation → [0 0 50]
  Medium Regulation → [25 50 75]
  Max Regulation → [50 100 100]

  Rules:
  High Load & High Drop → Max Regulation
  Low Load & Low Drop → No Regulation


Q9. Air Conditioner Compressor Speed Control

  Inputs:
  Indoor Temp (18–30°C) → Low [18 18 24], Medium [22 24 26], High [25 30 30]
  Occupancy (0 or 1) → Off [0 0 1], On [0 1 1]

  Output: Compressor Speed (0–100)
  Off → [0 0 0]
  Medium → [25 50 75]
  High → [50 100 100]

  Rules:

  Occupied AND High Temp → High Speed
  Unoccupied → Compressor Off
  Occupied AND Medium Temp → Medium Speed


Q10. Traffic Light Timing Controller

  Inputs:
  Traffic Density (0–100) → Low [0 0 50], Medium [25 50 75], High [50 100 100]
  Time of Day (0–24) → Off-Peak [0 0 12], Peak [8 16 24]

  Output: Green Signal Time (10–120s)
  Short → [10 10 60] 
  Medium → [30 60 90]
  Long → [60 120 120]

  Rules:
  Peak Hours & High Density → Green Long
  Off-Peak & Low Density → Green Short
  Medium Density → Green Medium
