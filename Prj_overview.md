1. System Overview
The program consists of a GUI for path creation, a path following algorithm, and a communication module to control the differential drive robot based on the desired trajectory. The main components are:
	• GUI for Path Drawing
	• Path Following Algorithm (Pure Pursuit)
	• Robot Control and Communication
	• Camera Input for Position Tracking
2. GUI for Path Drawing
	• Functionality: Create an intuitive interface that allows users to draw a path using mouse input. The drawn path can be saved and loaded.
	• Implementation:
		○ Use a library like Tkinter, PyQt, or Pygame for the GUI.
		○ Capture mouse events to allow freehand drawing of paths.
		○ Store path coordinates as a list of (x, y) points for later processing.
3. Path Following Algorithm (Pure Pursuit)
	• Overview: Implement the Pure Pursuit algorithm to calculate the necessary steering angles and speeds to follow the path drawn in the GUI.
	• Components:
		○ Path Representation: Convert the drawn path into a series of waypoints.
		○ Robot Localization: Utilize camera input to obtain the robot's current position (x, y) and orientation (angle).
		○ Pursuit Calculation: For a given lookahead distance, determine the closest waypoint and calculate the steering angle and speed.
	• Implementation:
		○ Continuously update the robot's position and recalibrate the path following based on its orientation and speed.
4. Robot Control and Communication
	• Overview: Send calculated PWM signals and control commands to the robot via the ESP32 for motor control.
	• Components:
		○ PWM Control: Calculate and generate PWM signals for the left and right motors based on the steering angle and speed.
		○ Torque Calculation: If needed, calculate torque requirements based on the robot's speed and path curvature.
		○ Communication Protocol: Use a communication protocol (like MQTT or HTTP) to send control commands from the computer to the ESP32.
	• Implementation:
		○ Establish a connection between the computer and ESP32 (e.g., Wi-Fi).
		○ Send commands in real-time based on the output from the Pure Pursuit algorithm.
5. Camera Input for Position Tracking
	• Overview: Use a camera to track the robot’s position and orientation in real-time.
	• Implementation:
		○ Utilize computer vision libraries (like OpenCV) to process the camera feed and detect the robot's position.
		○ Update the robot's (x, y) coordinates and orientation based on the detected features (e.g., colors or shapes).
6. Main Loop
	• Functionality: Continuously read the camera input, update the robot’s position, calculate the control commands using the Pure Pursuit algorithm, and send the commands to the robot.
	• Structure:
		○ Capture the current position and orientation from the camera.
		○ Update the robot's state and recalculate control commands.
		○ Send the commands to the ESP32 for execution.
		○ Repeat this process in a loop until the path is completed or the user stops the program.
7. Error Handling and Safety
	• Implement error handling to manage potential communication failures, unexpected inputs, or camera detection issues.
	• Add safety measures to stop the robot if it deviates too far from the path or if a critical error occurs.
Conclusion
This structured approach ensures that your program effectively integrates GUI design, algorithmic path following, and real-time control of the robot. By carefully implementing each component, you can create a responsive and accurate differential drive robot that follows paths drawn on your computer.
