# 🔍 Local Network Camera + WiFi Recon

This repo is my personal walkthrough of how I scanned my own local network to find hidden devices like IP cameras, routers, DVRs, and got the WiFi password using simple CMD and Nmap commands.

---

## 🧠 Why I Did This

I just wanted to understand how hackers can scan and attack WiFi-connected cameras or DVRs. All this is done on my **own network and devices**, nothing illegal.

---

## 🛠 Tools I Used

- `nmap` for scanning devices and ports
- VLC for viewing RTSP streams from camera
- Any Ip camera attached to your wifi router 
- Any wifi  router

---

## 🔐 How I Got My WiFi Password via CMD

📡 Nmap Scanning

Scan the full local network (mine was 192.168.29.0/24)
```bash
nmap -sP 192.168.29.0/24
```

Find open ports on a device (Your ip camera's Ip at for eg : 192.168.29.000)
bash
```
nmap -sV -sC -Pn 192.168.29.000 (change your actual ip here)
```

---

## 🎥 RTSP Stream of Camera
This was the main format that worked for my cameras , you have to see what actually worlks for your model number of the camera:

```bash
rtsp://admin:admin@192.168.29.121:554/cam/realmonitor?channel=1&subtype=0
```
Opened it in VLC → Media → Open Network Stream → paste the above


---

## 💀 Got error after too many tries:
account locked or please reboot in 24 hours

✅ Fixed it by rebooting the DVR manually.

## 📝 Notes
Nmap didn’t always return MAC vendors; some devices were unknown

RTSP required default creds (admin:admin) which locked after retries

Learned that UPnP, RTSP, and port 80/554 are very common in DVRs and IP cams
