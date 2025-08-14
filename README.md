# TASK 7: Monitor System Resources Using Netdata

### Objective
Install Netdata and visualize system and application performance metrics.

### Tools
* **Netdata**: A free, open-source monitoring tool.
* **Docker**: Used to run Netdata in a containerized environment.

---

### Step-by-Step Solution

# **1. Pull the Netdata Docker Image**
## Before you can run the container, you need to download the official Netdata image from Docker Hub.
---
 ## docker pull netdata/netdata
---
 # 2.  Run the Netdata Container

  docker run -d --name=netdata -p 19999:19999 \
--cap-add SYS_PTRACE \
--security-opt apparmor=unconfined \
netdata/netdata

 
Use the following command to run the Netdata container. The flags in this command are important for proper functionality:

* -d: Runs the container in detached mode (in the background).

* --name=netdata: Assigns the container the name "netdata" for easy management.

* -p 19999:19999: Maps port 19999 from the host to port 19999 in the container, allowing you to access the dashboard.

* --cap-add SYS_PTRACE and --security-opt apparmor=unconfined: These are required for Netdata to collect a full range of system metrics.

  # 3. Access the Dashboard
  ## Once the container is running, open your web browser and navigate to the following URL to see the real-time dashboard.

  ** url: http://localhost:19999
  ## The dashboard displays a comprehensive overview of your system, including CPU usage, memory usage, disk usage, and network statistics.

# 4.  Monitor System Metrics 
From the dashboard, you can explore various sections to monitor your system:

* System Overview: Check charts for CPU, RAM, and Disk performance.

* Applications: Identify which processes are using the most resources.

* Docker: Monitor the performance and status of your running Docker containers.
# 5. Explore Alerts and Panels
* Alerts: Look for red or yellow indicators on the charts that signal potential issues.

* Charts: Click on a chart to zoom in and analyze specific trends over time.

# 6.  View Logs
To access the Netdata logs within the container, use docker exec to run a command inside it.
``` bash
docker exec -it netdata bash
cat /var/log/netdata/error.log
cat /var/log/netdata/access.log
exit

