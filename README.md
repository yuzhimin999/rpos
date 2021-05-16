# rpos

Node.js based ONVIF Camera/NVT software that turns a Raspberry Pi, Windows, Linux or Mac computer into an ONVIF Camera and RTSP Server. It implements the key parts of Profile S and Profile T (http://www.onvif.org). It has special support for the Raspberry Pi Camera and Pimoroni Pan-Tilt HAT
基于Node.js的ONVIF摄像机/ NVT软件，可将Raspberry Pi，Windows，Linux或Mac计算机转换为ONVIF摄像机和RTSP服务器。 它实现了Profile S和Profile T（http://www.onvif.org）的关键部分。 它对Raspberry Pi相机和Pimoroni Pan-Tilt HAT具有特殊支持。

RPOS won an award in the 2018 ONVIF Open Source Challenge competition.
RPOS在2018年ONVIF开源挑战赛中获奖。

## History and Contributors

The initial goal (by @BreeeZe) was to provide a ONVIF Media service which is compatible with Synology Surveillance Station to allow the Raspberry Pi to be used as a surveillance camera without the need for adding any custom camera files to your Synology NAS.
First demo video @ https://youtu.be/ZcZbF4XOH7E
最初的目标（由@BreeeZe制定）是提供一种与Synology Surveillance Station兼容的ONVIF Media服务，以使Raspberry Pi可以用作监控摄像机，而无需向您的Synology NAS添加任何自定义摄像机文件。 第一个演示视频@ https://youtu.be/ZcZbF4XOH7E 

This version uses a patched version of the "node-soap" v0.80 library (https://github.com/vpulim/node-soap/releases/tag/v0.8.0) located @ https://github.com/BreeeZe/node-soap
此版本使用位于https://github.com/上的“ node-soap” v0.80库（https://github.com/vpulim/node-soap/releases/tag/v0.8.0）的修补版本。 BreeeZe /节点肥皂 


The next goal (by @RogerHardiman) was to implement more of the ONVIF standard so that RPOS could be used with a wide range of CCTV systems and with ONVIF Device Manager and ONVIF Device Tool. Additional ONVIF Soap commands were added including the PTZ Service with backend drivers that control the Raspberry Pi Pan-Tit HAT or emit various RS485 based PTZ protocols including Pelco D and Sony Visca.
下一个目标（@RogerHardiman提出）是实施更多的ONVIF标准，以便RPOS可以与各种CCTV系统以及ONVIF设备管理器和ONVIF设备工具一起使用。 添加了其他ONVIF Soap命令，包括带有后端驱动程序的PTZ服务，该驱动程序控制Raspberry Pi Pan-Tit HAT或发出各种基于RS485的PTZ协议，包括Pelco D和Sony Visca。 


Oliver Schwaneberg added GStreamer gst-rtsp-server support as third RTSP Server option.
Oliver Schwaneberg添加了对GStreamer gst-rtsp-server的支持，作为第三个RTSP Server选项。 


Casper Meijn added Relative PTZ support
Casper Meijn添加了相对PTZ支持
Johnny Wan added limited USB Camera support for GStreamer RTSP server.
Johnny Wan添加了对GStreamer RTSP服务器的有限USB摄像头支持。
If I've forgotten to put you in the list, please post an Issue Report and I can add you in.
如果我忘记了将您添加到列表中，请发布问题报告，然后我可以添加您。 

## Features:

- Implements the ONVIF Standard for a CCTV Camera and NVT (Network Video Transmitter)
- CCTV摄像机和NVT（网络视频发送器）实施ONVIF标准
- Streams H264 video over RTSP from the Official Raspberry Pi camera (the one that uses the ribbon cable) and some USB cameras
- 通过RSPberry Pi官方摄像头（使用带状电缆的摄像头）和一些USB摄像头通过RTSP传输H264视频
- Uses hardware H264 encoding using the GPU on the Pi
- 通过Pi上的GPU使用硬件H264编码
- Implements Camera control (resolution and framerate) through ONVIF
- 通过ONVIF实现摄像机控制（分辨率和帧率）
- Can set other camera options through a web interface.
- 可以通过网络界面设置其他相机选项。
- Discoverable (WS-Discovery) on Pi/Linux by CCTV Viewing Software
- 可通过CCTV观看软件在Pi / Linux上发现（WS-发现）
- Works with ONVIF Device Manager (Windows) and ONVIF Device Tool (Linux)
- 与ONVIF设备管理器（Windows）和ONVIF设备工具（Linux）一起使用
- Works with other CCTV Viewing Software that implements the ONVIF standard including Antrica Decoder, Avigilon Control Centre, Bosch BVMS, Milestone, ISpy (Opensource), BenSoft SecuritySpy (Mac), IndigoVision Control Centre and Genetec Security Centre (add camera as ONVIF-BASIC mode)
- 与其他实施ONVIF标准的CCTV观看软件配合使用，包括Antrica解码器，Avigilon控制中心，博世BVMS，Milestone，ISpy（开源），BenSoft SecuritySpy（Mac），IndigoVision控制中心和Genetec安全中心（将摄像机添加为ONVIF-BASIC）模式）
- Implements ONVIF Authentication
- 实施ONVIF身份验证
- Implements Absolute, Relative and Continuous PTZ and controls the Pimononi Raspberry Pi Pan-Tilt HAT
- 实现绝对，相对和连续PTZ，并控制Pimononi Raspberry Pi Pan-Tilt HAT
- Also converts ONVIF PTZ commands into Pelco D and Visca telemetry on a serial port (UART) for other Pan/Tilt platforms
- 还可以将ONVIF PTZ命令转换为用于其他水平/倾斜平台的串行端口（UART）上的Pelco D和Visca遥测
- Implements Imaging service Brightness and Focus commands (for Profile T)
- 实现成像服务的亮度和聚焦命令（针对配置文件T）
- Implements Relay (digital output) function
- 实现继电器（数字输出）功能
- Supports Unicast (UDP/TDP) and Multicast using mpromonet's RTSP server
- 使用mpromonet的RTSP服务器支持单播（UDP / TDP）和多播
- Supports Unicast (UDP/TCP) RTSP using GStreamer
- 使用GStreamer支持单播（UDP / TCP）RTSP
- Also runs on Mac, Windows and other Linux machines but you need to supply your own RTSP server. An example to use ffserver on the Mac is included.
- 也可以在Mac，Windows和其他Linux机器上运行，但是您需要提供自己的RTSP服务器。包括在Mac上使用ffserver的示例。
- USB cameras supported via the GStreamer RTSP server with limited parameters available. Tested with JPEG USB HD camera
- 通过GStreamer RTSP服务器支持的USB摄像机，但可用的参数有限。经过JPEG USB HD相机测试 


![Picture of RPOS running on a Pi with the PanTiltHAT and Pi Camera](RPOS_PanTiltHAT.jpg?raw=true "PanTiltHAT")
Picture of RPOS running on a Pi 3 with the PiMoroni PanTiltHAT and Official Pi Camera
！[使用PanTiltHAT和Pi摄像机在Pi上运行的RPOS的图片]（RPOS_PanTiltHAT.jpg？raw = true“ PanTiltHAT”）
使用PiMoroni PanTiltHAT和官方Pi相机在Pi 3上运行的RPOS的图片 
## How to Install on a Raspberry Pi:

For unbuntu 20.04

### STEP 2 - INSTALL NODEJS AND NPM
安装NODEJS和NPM 
NOTE: Node.js Version 6.x and 8.x have been tested with RPOS. Only a small amount of testing has been done with Node v10.
注意：Node.js版本6.x和8.x已通过RPOS测试。 Node v10仅进行了少量测试。 

#### STEP 2.1.a - INSTALL NODE USING NVM （使用NVM安装Node ubuntu 可以不安装）

You may choose to use [Node Version Manager (NVM)](https://github.com/nvm-sh/nvm) to install & use a specific version of Node & NPM, such as `nvm install 8` instead of the latest. Follow the instructions on NVM's github page to install & use.
您可以选择使用[Node Version Manager（NVM）]（https://github.com/nvm-sh/nvm）来安装和使用特定版本的Node＆NPM，例如`nvm install 8`，而不是 最新的。 请按照NVM的github页面上的说明进行安装和使用。 

#### STEP 2.1.b - INSTALL NODE USING APT

Pi and Linux users can install latest versions of Node and NPM together with this command:
Pi和Linux用户可以使用以下命令安装最新版本的Node和NPM： 
```
  sudo apt-get install npm
```

#### STEP 2.1.c - OTHER METHODS (其他方法，可以不考虑)

Windows and Mac users can install Node from the nodejs.org web site.

Older Raspbian users (eg those running Jessie) can install NodeJS and NPM with these commands
较老的Raspbian用户（例如，运行Jessie的用户）可以使用以下命令安装NodeJS和NPM 
```
  curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
  sudo apt-get install nodejs
```

#### STEP 2.2 - UPDATE NPM

If using [`NVM`](https://github.com/nvm-sh/nvm) to manage your Node.js version, the following will update NPM to the latest supported on your version of Node.js:
如果使用[`NVM`]（https://github.com/nvm-sh/nvm）管理您的Node.js版本，则以下内容会将NPM更新为您的Node.js版本支持的最新版本：

```
nvm install-latest-npm
```

Otherwise you can use NPM to update itself with this command:
否则，您可以使用NPM通过以下命令进行自我更新： 
```
sudo npm install -g npm@latest
```

Note this seemed to fail first time and needed to be ran twice to get my onto NPM version 6.7.0
请注意，这似乎是第一次失败，需要运行两次才能进入NPM 6.7.0版 

### STEP 3 - GET RPOS SOURCE, INSTALL DEPENDENCIES

```
git clone https://github.com/BreeeZe/rpos.git
cd rpos
npm install
```

### STEP 4 - COMPILE TYPESCRIPT(.ts) TO JAVASCRIPT(.js) using GULP

#### 4.1.a

For NPM version 5.2 and up, use the `npx` command to run the 'gulp' script:
第4步-使用GULP将TYPESCRIPT（.ts）编译为JAVASCRIPT（.js） 
```
npx gulp
```

#### 4.1.b

For older versions of NPM without `npx`, run the gulp script directly:
对于没有`npx`的旧版NPM，直接运行gulp脚本： 

```
./node_modules/gulp/bin/gulp.js
```

### STEP 5 - PICK YOUR RTSP SERVER （选择您的RTSP服务器 ）

Select & setup an RTSP option for your platform.
选择并设置适用于您平台的RTSP选项。 

RTSP Server options for Pi / Linux:
Pi / Linux的RTSP服务器选项：

1. RPOS comes with a pre-compiled ARM binary for a simple RTSP server. The source is in the ‘cpp’ folder. (option 1)
   RPOS带有用于简单RTSP服务器的预编译ARM二进制文件。 来源位于“ cpp”文件夹中。 （选项1）
2. mpromonet RTSP Server (option 2)
   mpromonet RTSP服务器（选项2）
3. GStreamer RTSP Server (option 3)
   GStreamer RTSP服务器（选项3）

RTSP Server options 2 & 3 offer more features, but require additional setup. See instructions below.
Currently USB camera is only supported by GStreamer RTSP Server
RTSP服务器选项2和3提供更多功能，但需要其他设置。 请参阅下面的说明。 目前，USB相机仅受GStreamer RTSP服务器支持。

Windows users will need to run their own RTSP Server.
Mac users can use the ffserver script.
Windows用户将需要运行自己的RTSP服务器。 Mac用户可以使用ffserver脚本。

Note: The choice of RTSP Server is made in rposConfig.json
注意：RTSP服务器的选择在rposConfig.json中进行 




#### STEP 5.a - OPTION 1: USING PRE-COMPILED ARM BINARY (deprecated)

This option is not recommended now. Please use Option 2 or Option 3
RPOS comes with a pre-compiled ARM binary for a simple RTSP server. The source is in the ‘cpp’ folder. No action required to use, this is pre-selected in `rposConfig.json`

Note that this option can be unstable, recommend option 2 or 3.

#### STEP 5.b - OPTION 2: USING MPROMONET RTSP SERVER

Raspberry Pi and Linux users will probably prefer the mpromonet RTSP server, as it has more options and supports multicasting.

Install dependencies and run setup script:

```
sudo apt-get install liblivemedia-dev
sh setup_v4l2rtspserver.sh
```

#### STEP 5.c - OPTION 3: USING GSTREAMER RTSP SERVER

Install the precompiled packages using apt, or compile them yourself for latest version.  
Installing the packages using apt saves a lot of time, but provides a rather old gstreamer version.

##### 5.c.1a - INSTALL GSTREAMER USING APT:

(For Raspberry PI camera)
```
sudo apt install git gstreamer1.0-plugins-bad gstreamer1.0-plugins-base \
 gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly \
 gstreamer1.0-tools libgstreamer1.0-dev libgstreamer1.0-0-dbg \
 libgstreamer1.0-0 gstreamer1.0-omx \
 libgstreamer-plugins-base1.0-dev gtk-doc-tools
```

(For USB camera, tested with Raspberry PI)
The default pipeline takes MJPEG from USB camera, decode it to Raw using omxmjpegdec, then encode it to H.264 using omxh264enc

Install GStreamer pipeline
```
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-omx-rpi gstreamer1.0-omx
```

Install Python Binding and gst-rtsp-server
```
sudo apt-get install python-gi gir1.2-gst-plugins-base-1.0 gir1.2-gst-rtsp-server-1.0
```

##### 5.c.1b - INSTALL GST-RPICAMSRC FROM SOURCE

(starting in /rpos root directory)

```
cd ..
git clone https://github.com/thaytan/gst-rpicamsrc.git
cd gst-rpicamsrc
./autogen.sh
make
sudo make install
cd ..
```

Check successful plugin installation by executing

```
gst-inspect-1.0 rpicamsrc
```

##### 5.c.2 - INSTALL GST-RTSP-SERVER FROM SOURCE

Next, compile gst-rtsp-server v1.4.5 (newer versions require newer GStreamer libs than those installed by apt)

```
git clone git://anongit.freedesktop.org/gstreamer/gst-rtsp-server
cd gst-rtsp-server
git checkout 1.4.5
./autogen.sh
make
sudo make install
```

Note: You do not need to load V4L2 modules when using rpicamsrc (option 3).

### STEP 6 - EDIT CONFIG

Rename or copy `rposConfig.sample-*.json` to `rposConfig.json`. (Choosing the appropriate sample to start with)

- Add a Username and Password for ONVIF access
- Change the TCP Port for the Camera configuration and the ONVIF Services
- Change the RTSP Port
- Enable PTZ support by selecting Pan-Tilt HAT or RS485 backends (Visca and Pelco D)
- Enable multicast
- Switch to the mpromonet or GStreamer RTSP servers
- Hardcode an IP address in the ONVIF SOAP messages

### STEP 7 - RUN RPOS.JS

#### First run (Skip with USB camera)

If you're using RTSP option 1 or 2, before you run RPOS for the first time you'll need to load the Pi V4L2 Camera Driver:

```
sudo modprobe bcm2835-v4l2
```

Initial setup is now complete!

#### Launch RPOS

To start the application:

```
node rpos.js
```

### STEP 8 - EXTRA CONFIGURATION ON PAN-TILT HAT (Pimononi)

The camera on the Pan-Tilt hat is usually installed upside down.
Goto the Web Page that runs with rpos `http://<CameraIP>:8081` and tick the horizontal and vertial flip boxes and apply the changes.

## Camera Settings

You can set camera settings by browsing to : `http://CameraIP:Port/`
These settings are then saved in a file called v4l2ctl.json and are persisted on rpos restart.
The default port for RPOS is 8081.
(Note that a lot of camera settings are now ignored by USB camera)

## Known Issues

- 1920x1080 can cause hangs and crashes with the original RTSP server. The mpromonet one may work better.
- 1920x1080 can cause encoding issue with USB camera pipeline. 1280x720 is recommended now.
- Not all of the ONVIF standard is implemented.

## ToDo's (Help is Required)

- Add MJPEG (implemented in gst-rtsp-server but still needs to return the correct ONVIF XML for MJPEG)
- Support more parameters for USB cameras with GStreamer RTSP server [work underway by RogerHardiman. Help needed]
- Support USB cameras with the Pi's Hardware H264 encoder (OMX) and the mpromonet RTP server (see https://github.com/mpromonet/v4l2tools)
- Implement more ONVIF calls (Events, Analytics)
- Test with ONVIF's own test tools (need a sponsor for this as we need to be ONVIF members to access the Test Tool)
- Add GPIO digital input
- Add two way audio with ONVIF back channel. We understand GStreamer has some support for this now.
- and more...
