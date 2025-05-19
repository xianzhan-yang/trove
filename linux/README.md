## display a "Today's Tasks" message when logging into a Linux system

---

### ✅ 1. Show tasks on terminal login using ~/.bash_profile or ~/.bashrc

These files are executed when a user logs into the shell:
Edit your .bash_profile or .bashrc:
```bash
nano ~/.bash_profile
```
or
```bash
nano ~/.bashrc
```
Add this at the end:
```bash
echo "==== Today's Tasks ===="
cat ~/tasks/today.txt
echo "========================"
```
Make sure the file ~/tasks/today.txt exists and contains your daily tasks.

## ✅ 2. Use /etc/motd for static messages (Message of the Day)

This message is shown during SSH or terminal login:
```bash
sudo nano /etc/motd
```
Example content:
```bash
Welcome to the system!
==== Today's Tasks ====
- Review logs from yesterday
- Submit daily report
- Prepare for team meeting
```
This file is static, so it's good for general reminders.

### ✅ 3. Use /etc/profile.d/ for dynamic system-wide scripts (recommended)

Create a script to run on login for all users:
```bash
sudo nano /etc/profile.d/show_tasks.sh
```
Add:
```bash
#!/bin/bash
echo "==== Today's Tasks ===="
cat /etc/today_tasks.txt 2>/dev/null || echo "No tasks for today."
echo "========================"
```
Make it executable:
```bash
sudo chmod +x /etc/profile.d/show_tasks.sh
```
Create the task file:
```bash
sudo nano /etc/today_tasks.txt
```

### 🖥️ Bonus: Show tasks on GUI login (desktop environment)

If you're using GNOME, KDE, etc., you can display a popup using zenity:
```bash
zenity --info --title="Today's Tasks" --text="$(cat ~/tasks/today.txt)"
```
Add that command to:
- ~/.xprofile
- or your desktop session’s Startup Applications
