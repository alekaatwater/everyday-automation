# Daily System Health Check

## Overview
A lightweight Python script that automatically checks the health of your system and generates a timestamped report. Instead of manually checking your CPU, memory, and disk usage, this script does it all in one run and saves the results for your records. Useful for anyone who wants a quick daily snapshot of their system without opening multiple tools.

## The Problem
Most users have no visibility into how their system is performing day to day until something goes wrong. By then it is too late. This script solves that by giving any user a clear, readable health report in seconds so they can catch issues like low disk space or high memory usage before they become real problems.

## Requirements
- Python 3
- psutil library

Install the required library by running:

```
pip3 install psutil
```

## How to Run

Navigate to the folder where the script is saved and run:

```
python3 system_health_check.py
```

The report will print to your terminal and automatically save as a timestamped txt file in the same folder.

## What It Checks

- **CPU Usage** — flags if usage exceeds 80%
- **Memory Usage** — flags if usage exceeds 80%
- **Disk Space** — flags if usage exceeds 85%
- **System Uptime** — shows how long the system has been running
- **Top 5 Processes** — lists the processes consuming the most CPU
- **Summary** — clearly states whether all systems are healthy or lists any warnings

## Sample Output

```
=======================================================
       DAILY SYSTEM HEALTH REPORT
=======================================================
  Generated : 2026-03-24 06:33:33
  Hostname  : your-macbook
  OS        : macOS
  Uptime    : 2d 4h 15m

── CPU ────────────────────────────────────────────────
  Usage     : 23.0%  ✅ OK
  Cores     : 8

── MEMORY ─────────────────────────────────────────────
  Usage     : 61.0%  ✅ OK
  Used      : 9.76 GB / 16.00 GB
  Available : 6.24 GB

── DISK (/) ───────────────────────────────────────────
  Usage     : 74.0%  ✅ OK
  Used      : 370.00 GB / 500.00 GB
  Free      : 130.00 GB

── TOP 5 PROCESSES BY CPU ─────────────────────────────
   1234  Chrome                     CPU:  12.3%  MEM:  4.1%
   5678  Slack                      CPU:   5.1%  MEM:  2.3%

── SUMMARY ────────────────────────────────────────────
  ✅ All systems operating within normal thresholds.
=======================================================
```

## Optional: Schedule It to Run Daily
To automate this script every morning on Mac, add a cron job by running `crontab -e` in your terminal and adding:

```
0 9 * * * python3 ~/Downloads/system_health_check.py
```

This runs the script automatically at 9:00 AM every day.

## Technologies Used
- Python 3
- psutil
- platform
- datetime
- os
