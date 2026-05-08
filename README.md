# Sleep_Disturbance_Monitor
## What is it?
This project implements a basic sleep disturbance monitoring system using the MySignals platform. It monitors three physiological and behavioral indicators that may be related to disturbed sleep: snoring, skin conductance, and body position changes.
## Sensors used:
- Snore sensor: detects possible breathing or snoring disturbance.
- GSR sensor: measures skin conductance, which may increase during physiological arousal.
- Body position sensor: detects changes in sleeping position.
## How the code works: 
Every 5 seconds, the system combines the scores from the three sensors and displays a final disturbance level on the MySignals TFT screen: LOW, MEDIUM, or HIGH.

- The code begins by initializing the MySignals board, the snore sensor, the body position sensor, and the TFT LCD display. The LCD is used to show the current sensor readings and the final sleep disturbance verdict.

- Instead of using delay(), the program uses millis() to run the main sensor-reading logic once every second. This allows the system to keep timing more cleanly without fully stopping the Arduino program.
- During each 1-second sample, the code reads: The snore voltage, the GSR conductance value, the current body position code.
- Each snore and GSR reading is converted into a score using threshold-based functions. These scores are accumulated over a 5-second monitoring window.

- The body position logic includes a simple noise filter. A new position is not counted immediately. Instead, the code waits until the new position appears twice before counting it as a real movement. This avoids counting quick flickering or noisy sensor readings as actual body movement.

After 5 samples, the system calculates the Final Verdict.
## Note about calibration:
The thresholds used in this code are demonstration values. For a real sleep monitoring system, the snore and GSR thresholds would need to be calibrated using real sensor data and tested over a longer monitoring period.

The 5-second window is also used for demonstration purposes. In a real sleep monitoring application, a longer window such as 30 seconds or more would provide more reliable results.

## Limitations:

This project is a prototype and is not intended for medical diagnosis. The sensor thresholds are not clinically validated, and the system only gives a basic indication of possible sleep disturbance. More advanced filtering, calibration, and longer-term data analysis would be needed for real-world use.

[Sleep_Disturbance_Monitoring.txt](https://github.com/user-attachments/files/27516681/Sleep_Disturbance_Monitoring.txt)
