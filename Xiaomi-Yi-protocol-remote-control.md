Research of Xiaomi Yi protocol
============
7878 - remote control port, use JSON 
[PC/Mac/Linux Python GUI](https://github.com/deltaflyer4747/Xiaomi_Yi/tree/master/Standalone_scripts)

<cut>
Opened ports on 192.168.42.1
========
Discovered open port 80/tcp on 192.168.42.1
Discovered open port 554/tcp on 192.168.42.1
Discovered open port 53/tcp on 192.168.42.1
Discovered open port 8787/tcp on 192.168.42.1
Discovered open port 7878/tcp on 192.168.42.1

 - 80 - http access (for download files via Wi-Fi http://192.168.42.1/DCIM/100MEDIA/)
 - 7878 - remote control port, use JSON 

7878 JSON
====
Use 
 > telnet 192.168.42.1 7878

Access token
----
Request:
 > {"msg_id":257,"token":0}

Answer:
 > { "rval": 0, "msg_id": 257, "param": 1 }

param=1, 1 is a TOKEN, it could be any other INT (or string? or something else?)

Camera config
--------
Request:
 > {"msg_id":3,"token":1}

Answer:
 > { "rval": 0, "msg_id": 3, "param": [ { "camera_clock": "2015-04-07 02:32:29" }, { "video_standard": "NTSC" }, { "app_status": "idle" }, { "video_resolution": "1920x1080 60P 16:9" }, { "video_stamp": "off" }, { "video_quality": "S.Fine" }, { "timelapse_video": "off" }, { "capture_mode": "precise quality" }, { "photo_size": "16M (4608x3456 4:3)" }, { "photo_stamp": "off" }, { "photo_quality": "S.Fine" }, { "timelapse_photo": "60" }, { "preview_status": "on" }, { "buzzer_volume": "mute" }, { "buzzer_ring": "off" }, { "capture_default_mode": "precise quality" }, { "precise_cont_time": "60.0 sec" }, { "burst_capture_number": "7 p / s" }, { "restore_factory_settings": "on" }, { "led_mode": "all enable" }, { "dev_reboot": "on" }, { "meter_mode": "center" }, { "sd_card_status": "insert" }, { "video_output_dev_type": "tv" }, { "sw_version": "YDXJv22_1.0.7_build-20150330113749_b690_i446_s699" }, { "hw_version": "YDXJ_v22" }, { "dual_stream_status": "on" }, { "streaming_status": "off" }, { "precise_cont_capturing": "off" }, { "piv_enable": "off" }, { "auto_low_light": "on" }, { "loop_record": "off" }, { "warp_enable": "off" }, { "support_auto_low_light": "on" }, { "precise_selftime": "5s" }, { "precise_self_running": "off" }, { "auto_power_off": "5 minutes" }, { "serial_number": "xxxxx" }, { "system_mode": "capture" }, { "system_default_mode": "capture" }, { "start_wifi_while_booted": "off" }, { "quick_record_time": "0" }, { "precise_self_remain_time": "0" }, { "sdcard_need_format": "no-need" }, { "video_rotate": "off" } ] }

Photo capture
-------
Request:
 > {"msg_id":769,"token":1} 

Answers:
 > { "msg_id": 7, "type": "start_photo_capture" ,"param":"precise quality;off"}
 > { "msg_id": 7, "type": "photo_taken" ,"param":"/tmp/fuse_d/DCIM/100MEDIA/YDXJ0047.jpg"}

photo will be stored on SD card as DCIM/100MEDIA/YDXJ0047.jpg

Video stream
==========
Video stream could be activated via YiCamera application, after activation stream rtsp://192.168.42.1/live will be available for VLC or any other uitable application. Stream is h.264 640x480

![pic1](https://github.com/SovGVDWebsites/copter.sovgvd.info/blob/main/pics/ab4/858/ab485818ce9af6b0307890a0304391a9.png?raw=true)

![pic2](https://github.com/SovGVDWebsites/copter.sovgvd.info/blob/main/pics/631/5cf/6315cffb793a1c2ef961f3fdea874a86.png?raw=true)


RAW requests and answers
============
download - sorry, lost file =(

too lazy for remove my serial number =)


Also look at [this research](https://github.com/vogloblinsky/elmo-qbic-4-cam-rig-manager/blob/master/API_Reverse_engineering.md) 
