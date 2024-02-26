# Real-Time Healthcare Dashboard

This project implements a real-time health dashboard and coordination system leveraging WebSocket communication between patients, doctors, and ambulance services.

## Key Components
**User Servlet**

The UserServlet handles authentication and session management. It processes the username from the login page and sets up the user session according to assigned roles - doctor, patient, or ambulance. This provides the foundation for access control across the rest of the application.

**VitalCheckEndPoint**

This WebSocket server endpoint is the central communication hub. It maintains connections with clients, receives vital signs updates from patients, evaluates thresholds to determine alerts, and routes notification messages to appropriate connected doctors, patients, and ambulances based on analysis of real-time data.

**VitalCheckConfigurator**

The configurator propagates the user identity and role information from the Servlet login session into each WebSocket session for a unified view of users across the layers. This allows the VitalCheckEndPoint to manage permissions on vital updates and message routing.

**index.html**

Simple login page to enter username

**doctor.jsp**

This page serves as the doctor's monitoring dashboard displaying patient metrics as they stream in and allowing doctors to take actions like prescribe medication or summon ambulance by sending messages to related user sessions.

**patient.jsp**
The patient view is for submission of real-time oxygen level, body temperature and getting alerts when doctor initiates medical interventions. Patients can see medication suggestions posted by their assigned healthcare provider.

**ambulance.jsp**
The ambulance staff portal displays pending requests for patient hospital transports. Alert popups notify drivers of new cases submitted by doctors so immediate attention and dispatch can happen.
