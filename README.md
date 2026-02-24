# **SHIELD**  —  *Stagnant-water Hazard Identification & Electrical Leakage Detector*  
## Problem
During monsoon or after heavy rains, stagnant water often collects around street‑light poles. If a live conductor leaks into the pole or the surrounding water, it can raise the water’s potential to dangerous levels, risking electrocution for pedestrians and animals. Municipal teams need a simple, self‑powered early‑warning device that detects increasing water conductivity (as a proxy for risk) and alerts the neighborhood instantly.
## One‑Line Solution 
A solar‑powered, always‑on sensor head with stainless electrodes uses a and an Arduino Nano to monitor water conductivity. The system simulates a safe “fault injection” by applying a small alternating signal into the water. If conductivity rises beyond a safe threshold (e.g., due to salt or contaminants), the system triggers a loud buzzer and a flashing red beacon.

## How It Works (Overview) 
- One electrode will be used by the  **external DC source**  to send a very small, safe  **signal**  into the water.  (simulating cureent leak) 
- The second electrode will act like a  **listener** . If the water is clean and not very conductive, the listener hardly picks up anything. But if the water has become conductive (due to salt, dirt, or a leak from the lamppost), then this electrode  
The Arduino reads this safe, reduced signal and compares it against a  **preset threshold** . If the water’s potential crosses this danger line, and stays above it for a couple of seconds, the Arduino immediately switches on a  **piezo buzzer**  and a  **flashing LED**  **and cut off the power of the lamp** . 

## Why This Design 
- It is  **simple** , because the only real parts we need are the Arduino Nano, resistors, one capacitor, two electrodes, a buzzer and an LED. 
- It is  **effective** , because the system only reacts when the water actually carries a dangerous potential. 

## Detection Logic 
- ## Power Setup: External 3.7V DC battery sends small current through water via one electrode  
- ## Detection: Second electrode picks up the signal → reads it through Arduino pin A0 
## **What the numbers mean:** 
- ## SAFE: Reading below 600 = Clean/pure water (no leakage) 
- ## MILD: Reading 600–650 = Slightly dirty water (system ignores this) 
- ## DANGER: Reading 650 or higher = Salty/conductive water detected (possible electrical leak!) 
- ## How it checks: Takes 20 measurements and averages them every half second to avoid false alarms 
## Future Upgrades
- Wireless alert: LoRa/SIM to notify teams
- Data logging: SD card/cloud dashboard
- Self‑test: electrode and battery health
- Field deployment: isolated AC sensing for real leaks 
