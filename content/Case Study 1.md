---
title: IoT Inventory Management
tags:
---
#Inventory #IoT #UI_Design #UX_Research #Team #Arduino 

## Overview

This was a month long student project for the course of IoT. Our team consisted of 6 people. My role was to create the UI/UX of the student interface. I also helped in overall strategy, training the image recognition model and creating the demo video. 

> [!insight] 
> 
> The primary objective of our IoT-based inventory management system was to reduce wastage and streamline the issuing and returning processes of design materials at SSD (Somaiya School of Design). These materials ranged from expensive items like ink and oil paints to inexpensive ones like paperclips and pencils, all provided free of charge to students.

## Problem Analysis

Tracking Issues  
The SSD inventory lacked an accurate method of tracking issued and returned items. which led to Bulk buying due to poor tracking, Misuse and loss of materials and Wasted resources.  
  
Student Behavior  
Students were impatient and reluctant to log small item issuances in the physical ledger. Many would skip this step altogether, particularly for cheaper items like paper and glue sticks which they might need for a short duration. The ledger itself was often misplaced.  
  
Caretaker Overload  
The inventory caretaker spent significant time searching for items, managing irresponsible students, and manually tracking stock levels through visual inspection. This often resulted in last-minute restocking and bulk purchasing, as it was sometimes faster and cheaper to buy new items than to find existing ones in storage.

## Research

Innovative Models  
We drew inspiration from systems like Amazon Go, Amazon Fresh, and self-checkout processes. We studied these systems to develop an efficient, user-friendly approach to material issuing and returning.  
  
Stakeholder Interviews  
We conducted interviews with students, caretakers, procurement staff and instructors to better understand the pain points and needs of each group. We also analyzed the physical ledger to track usage patterns and identified that most items not returned were in the low-cost category (we are excluding materials like paper that get used up in projects).

## Proposed Solution

Categorisation of Items  
Based on our analysis, we divided inventory into three categories:

Low priority- Commonly used by design students on a daily basis, such as scissors, cutters, and tape.

Mid priority- occasionally used by students and range in price from around 300 to 1500 rupees.

High priority tools and resources priced above 1000 rupees, often with limited availability.

Decentralising Low Priority Items  
To reduce wastage and misuse, we placed low-priority items directly in classrooms. Each class was given a fixed stock of these materials to manage. This shift:  

- Eliminated the need for students to write in the ledger for small items
- Simplified the return process by eliminating it for low-priority items
- Enabled tracking of each class's monthly usage, helping identify wastage or potential theft at a granular level

  
IoT Integration and Image Recognition  
For higher-value materials, we implemented an IoT-enabled system using RFID cards and motorised locks. The issuing process was simple:  

- Students scan their RFID card to log in, which triggers the CCTV and unlocks the cabinet.
- Students select items from the cupboard, place them on a scanning tray, and close the door.
- An onboard camera uses image recognition AI to identify the item on the tray, which is then logged into the system.
- The student confirms the issuance and leaves with the item.

  
Security  
The system ensures that students can’t scan one item and take another. The return process involved scheduled return slots where a caretaker was present to ensure items were returned properly.

We had to strike a balance between ease of use and system security. If the process was too complex, students might avoid returning items altogether, but a lax system could lead to theft. Our solution included surveillance and an efficient issuing process that prevented misuse while being user-friendly enough to encourage compliance.  
  
The key sweet spot was the image recognition system, which replaced the tedious process of manually logging items in a ledger. This not only reduced misuse but also made the process faster and less cumbersome for students.

## Prototyping

For the student interface UI/UX, I drew inspiration from our college library’s book issuing system. The always-on login screen, ID card scanning, and item checkout process were adapted to fit our scenario. Usability heuristics, such as visibility of system status through breadcrumbs and guides, user control, and consistency, were prioritized.  
  
Initial prototypes included a 'recent activity' tab, but user testing revealed confusion, so we moved it to the returns section. We also added an option for users to check item availability before logging in.  
  
For the physical components, we used an RFID scanner connected to NodeMCU (Master) and a servo motor to NodeMCU (Slave). After scanning an ID, the NodeMCU (Master) filters the necessary data, uploads it to Google Sheets, and commands NodeMCU (Slave) to turn the servo for storage access. The image recognition model, trained with Google’s Teachable Machine, identifies items on a webcam feed, simplifying item detection.

RFID Scan

In the video below, Nikita scans my College ID card using an RFID scanner module connected to a NodeMCU IoT device. This NodeMCU is linked to a Google Sheets file via an API key. Upon scanning the ID, the system records the name and timestamp in the Google Sheets file.

Image Recognition

In the video below, I place items on a tray under a webcam connected to a laptop. The video feed is processed by p5.js, which incorporates a Google Teachable Machine model. This model identifies the items and displays their names on the screen.

Locking/Unlocking

In the video below, after scanning the College ID card, the NodeMCU sends a command to another NodeMCU equipped with a servo to lock or unlock. The NodeMCU also adds the Name and timestamp of the user to the google sheets file.

Considerations

Interface Design  
The system used a 13" touchscreen interface with large, easy-to-press buttons to accommodate gross motor actions (as opposed to fine motor actions typically seen in phone use). The UI was customized with SSD branding, using minimalistic design and high contrast for clarity. The UX was designed to mimic familiar e-commerce experiences, ensuring ease of use for students.  
  
Prioritizing Speed and Simplicity  
Most users would be interacting with the system to issue mid-priority items, so the primary call-to-action button was prominently displayed, reducing cognitive load and minimizing the chance of misclicks.  
  
Technical Considerations  
We used NodeMCU for the IoT prototype, which allowed for wireless communication between the RFID scanner and the motorized lock. This setup enabled us to place components at a distance, offering greater flexibility in the design of the physical space.

Next Steps

Automation and Modularity  
The goal for future iterations was to make the system modular, scalable, and capable of automatically ordering low-stock items. With full IoT integration, the need for a physical caretaker could be minimized, offering a more streamlined and autonomous inventory management system.  
  
Training the Model  
While the image recognition model was trained in minutes during the prototype phase, a professional system would significantly reduce this time. Once trained, the caretakers could easily manage inventory without the burden of monitoring returns and issuing processes.  
  
Behavioral Solutions  
One of the behavioral challenges we considered was theft or failure to return items. One idea was to add price tags next to each item being issued to remind students of the cost. However, this was discarded due to varying perceptions of item value. Instead, we focused on surveillance and the seamless, accountable system to discourage theft.

## Learnings

Technical Hurdles  
One of the main challenges was ensuring the technical components worked seamlessly together. Connecting multiple devices, such as the RFID scanner, NodeMCU, and image recognition system, required significant troubleshooting and trial and error.  
  
Design Impact  
The technical limitations and behavioral challenges we faced heavily influenced our design choices. For example, the image recognition system was chosen not only for its accuracy but also to replace the inefficient manual process of logging materials.