# Welcome to Lab 2 - Sniffing all the Trons

Professor: [William Cox](www.liquidswrds.com)  
University: University of Arkansas at Little Rock

## Table of Contents

- [Welcome to Lab 2 - Sniffing all the Trons](#welcome-to-lab-2---sniffing-all-the-trons)
  - [Table of Contents](#table-of-contents)
  - [Objective](#objective)
  - [Tools](#tools)
  - [Lab Artifacts](#lab-artifacts)
    - [Lab Report Formatting](#lab-report-formatting)
  - [Lab Credentials](#lab-credentials)
  - [Task 1: Capturing Network Traffic](#task-1-capturing-network-traffic)
    - [Task 1 Overview](#task-1-overview)
    - [Task 1 Instructions](#task-1-instructions)
  - [Task 2: Analyzing Network Traffic with Wireshark](#task-2-analyzing-network-traffic-with-wireshark)
    - [Task 2 Overview](#task-2-overview)
    - [Task 2 Instructions](#task-2-instructions)
  - [Task 3: Arkime](#task-3-arkime)
    - [Task 3 Overview](#task-3-overview)
    - [Task 3 Instructions](#task-3-instructions)

## Objective

This lab is designed to help you understand the different types of protocols found on typical corporate networks and how they can be captured and analyzed. You will be introduced to different network analysis tools through out this lab with the intent of allowing you real world hands on experience with network traffic analysis.

## Tools

- Operating System: Debian 12
- Network Analysis Tools:
  - Arkime
  - tcpdump
  - WireShark

## Lab Artifacts

Build a Lab report file with the requested answers or screenshots presented in this lab.

### Lab Report Formatting

When completing your lab please follow these formatting instructions.

1. Labs files will be formatted as Times New Roman, 12 Font.
2. Create a title page with the following details:
   1. Title of the Lab
   2. Class Name
   3. Your name
   4. Date
3. Section 2 will have all screenshots and questions/answers for the lab.
   1. Each question must be listed with its question number.
   2. Answers will be indented on the next line and start with an "a."
   3. If answer includes a picture, make sure picture is big enough for your instructor to interpret, but not too big to distract from the quality of your work.
4. Section 3 will be labeled Reflection.
   1. This is where you add any reflections needed.
   2. Make sure to quote your sources with parenthetical/in text citations.
   3. Do not use quotes, but instead rewrite the quote in your own words. Remember to still give credit to the author.
5. Section 4 will be References
   1. All references should be in alphabetical order
   2. Use any citation style you prefer, but be consistent. (APA, MLA, IEEE., etc.)

## Lab Credentials

Username: `student`
Password: `CSEC2324_Student!`

## Task 1: Capturing Network Traffic

### Task 1 Overview

In this task, you will use the `tcpdump` command to capture network traffic on your computer. `tcpdump` is a command-line packet analyzer that allows you to capture network traffic on a network interface. You will capture network traffic while visiting a website and analyze the captured traffic.

### Task 1 Instructions

1. Open a terminal and run the following command to start capturing network traffic using tcpdump.

    ```bash
    sudo tcpdump -i ens4 -w capture.pcap
    ```

   - ***Pro Tip:** This command will write the output to your hard drive, so make sure not to take too much time to complete step 1-3.*
   - **Explanation:** This command will start the program `tcpdump` with root (administrative) permissions and will capture network traffic on the interface `ens4` and write the output to a file called `capture.pcap`.
2. Next, minimize your terminal and open Firefox, then navigate to `https://ualr.edu/computerscience/cybersecurity-programs/`.
3. When the webpage is loaded, stop the tcpdump process by maximizing your terminal pressing `Ctrl+C`.

    - **Explanation:** `Ctrl+C` is a keyboard shortcut that will send a signal to the running process to stop. In our case, we are sending a signal to the tcpdump process to stop capturing network traffic. Since we started the tcpdump process with the `-w` flag, the output will be written to a file called `capture.pcap`.
4. Let's see what we captured. Run the following command to view the contents of the `capture.pcap` file:

    ```bash
    tcpdump -r capture.pcap
    ```

   - **Explanation:** This command will read the contents of the `capture.pcap` file and display the captured network traffic on the terminal.
5. What do you see in the output? Take a screenshot of the first few lines of the output and save it to your lab report. Include the line that shows your command.
   - The output can be very long depending how long you took to capture the traffic.
6. Answer the following questions and add them to your lab report.**Please include a screenshot showing the answers to the questions.** The screenshot should have the answer higlighted in a way to show the specific answer to the question.:
   1. Find the traffic that originated from your computer and destination to the website in step 2.
      1. What is the IP address of your computer?
      2. What is the destination IP address of the captured traffic?
      3. What protocols are used in the captured traffic? Hint: There will be more than 1 protocol.

## Task 2: Analyzing Network Traffic with Wireshark

### Task 2 Overview

Lets analyze the captured traffic using Wireshark. Wireshark is a network protocol analyzer that can capture and display the data traveling back and forth on a network. It can be used to troubleshoot network problems, examine security problems, and monitor network traffic.

Pros of using Wireshark:

- It is free and open-source.
- It is available for Windows, macOS, and Linux.
- There are many tutorials and resources available online.

Cons of using Wireshark:

- Wireshark runs in memory, so it can be resource-intensive.

### Task 2 Instructions

1. Open Wireshark by clicking on the wirshark icon on the desktop.
2. Click on `File` and then `Open` to open the `capture.pcap` file.
3. Familiarize yourself with the Wireshark interface. Go to the following website to learn more about the Wireshark interface: [Wireshark User Interface (GUI) Overview](https://networkproguide.com/wireshark-user-interface-gui-overview/).
4. Let's apply a filter to the captured traffic. In the filter bar, type `http` and press `Enter`.
5. What do you see in the output? Take a screenshot of the first few lines of the output and save it to your lab report. Include the line that shows your command.
   - The output can be very long depending how long you took to capture the traffic.
6. Research different filters and answer the following questions. Add a screenshot showing your filter and the output:
   1. What is the filter to display only the traffic that originated from your computer?
   2. What is the filter to display only the traffic that is destined to the website in step 2?
   3. What is the filter to only show traffic from your computer to the website in step 2?  
      *Hint: This is different from the previous two questions.*
   4. What is the sequence number for the very first packet in the captured traffic?
7. Next lets look at statistics of the captured traffic. Clear all of your filters by clicking on the `Clear` button in the filter bar.
8. Click on `statistics` and then `Protocol Hierarchy`. Take a screenshot of the output and save it to your lab report.
9. Answer the following questions and add them to your lab report.**Please include a screenshot showing the answers to the questions.** The screenshot should have the answer higlighted in a way to show the specific answer to the question.:
   1. What is the most used protocol in the captured traffic?
   2. What is the least used protocol in the captured traffic?
   3. What is the total number of packets captured?
   4. What is the total number of bytes captured?
10. Next lets look at the conversations in the captured traffic. Click on `Statistics` and then `Conversations`. Take a screenshot of the output and save it to your lab report.
11. Answer the following questions and add them to your lab report.**Please include a screenshot showing the answers to the questions.** The screenshot should have the answer higlighted in a way to show the specific answer to the question.:
    1. What is the IP address of the computer that sent the most packets?
    2. What is the IP address of the computer that received the most packets?
    3. What is the total number of packets sent by the computer that sent the most packets?
    4. What is the total number of packets received by the computer that received the most packets?

## Task 3: Arkime

### Task 3 Overview

Arkime is a network traffic analysis tool that allows you to capture, index, and search network traffic. It is a powerful tool that can be used to analyze network traffic in real-time or from a pcap file. In this task, you will use Arkime to analyze the captured traffic.

### Task 3 Instructions

