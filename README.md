# CSN 150 Midterm-Project

## ESP32 as a WiFi Intrusion Detection System

## by Emmanuel Apeatu and Pooran Dunraj

## Purpose
The purpose of this project is to utilize ESP32 as a WiFi Intrusion Detection System. It will detect and log the unkown mac address of machines connecting to an assigned Wifi.

## Equipment
An ESP32 and a computer is required to perform this project.

## What does the project do?  
This project uses an ESP32 as a device to detect machines trying to connnect to a Wifi it is assigned to. 

## Why do you find it interesting?
We found this project interesting because it is an easy way to create an IDS for personal home network usage.

## Steps we followed
Steps Followed for Logging Unknown MAC Addresses
1. Setup Environment:
We used Arduino IDE and set up the ESP32 board via the Board Manager.

2. Code Structure:
Included necessary libraries: WiFi.h and WebServer.h.

3. Wi-Fi Configuration:
Defined the SSID and password for the Wi-Fi network.
Connected the ESP32 to the Wi-Fi network using WiFi.begin(ssid, password).

4. Web Server Initialization:
Initialized a web server on port 80 using WebServer server(80);.
Defined a route for the root URL with a handler function (handleRoot).

4. MAC Address Scanning:
Used WiFi.scanNetworks() to scan for nearby devices.
Retrieved the MAC address of each detected device using WiFi.BSSIDstr(i).

5. Known MAC Address Checking:
Implemented the isKnownMac(String macAddress) function to check if the detected MAC address is in a predefined list of known MAC addresses.

6. Logging Unknown MAC Addresses:
If an unknown MAC address was detected, it was logged into a string variable (logMessage).
Printed the unknown MAC address to the Serial Monitor for debugging purposes.

7. Web Server Response:
Updated the handleRoot function to send the logged unknown MAC addresses to the web browser when accessing the ESP32's IP address.

8. LED Indication:
Used an LED to signal the detection of an unknown MAC address by turning it on for a short duration. 

## Problems
Note your problems or errors here.  Google any error you may come across, and not what you tried (even if it does not work), and what was the final answer.
1. MAC Address Not Detected:
Issue: Unknown MAC addresses were not being logged correctly.
Solution: Checked the loop where MAC addresses are retrieved to ensure it processed all detected devices and appended unknown addresses to logMessage.

2. Serial Monitor Output:
Issue: Serial Monitor was printing logs instead of sending them to the web server.
Solution: Verified that the handleRoot function returned the content of logMessage instead of only printing it.

3. Web Server Not Responding:
Issue: The web server sometimes didn’t respond with the correct log data.
Solution: Ensured server.handleClient() was called in the loop to process incoming requests and that the correct status code and content type were set in server.send().

4. Code Compilation Errors:
Issue: Errors related to undefined functions or types.
Solution: Checked the code for typos and ensured all necessary libraries were included and properly referenced.
