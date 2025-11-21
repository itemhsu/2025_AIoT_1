# AIoT_one
AIoT第一堂

## ESP32-P4-EYE 視覺開發板概要

* 基於 ESP32-P4 RISC-V 雙核心處理器
* 支援 最高 32 MB PSRAM
* 內建多媒體與高速介面：
  * USB 2.0
  * MIPI-CSI / MIPI-DSI
  * H.264 硬體編碼器
* 適用高效能、低功耗、多媒體與 IoT 應用

### 無線通訊功能
* 搭載 ESP32-C6-MINI-1U 模組
* 用於 Wi-Fi 6 與 Bluetooth LE 通訊
* 支援 USB 2.0 High-Speed Device Mode

### 板載硬體功能
* MIPI-CSI 相機介面
* 內建相機模組
* 麥克風（音訊輸入）

### MicroSD 卡擴充
* 整合影像與音訊資料的擷取、儲存與即時處理能力

## 應用場景
 * 智慧安防攝影機
 * 視覺模型推論 / 偵測
 * IoT 邊緣運算
 * 即時影像處理與無線傳輸設備

## 外觀
<img width="2591" height="2167" alt="image" src="https://github.com/user-attachments/assets/d200ffe2-41a3-45ca-84b1-8a7b22ac996a" />
<img width="2209" height="1985" alt="image" src="https://github.com/user-attachments/assets/94f9e326-58f2-4869-8248-5b0be43d570b" />


## 組件介紹
<img width="898" height="556" alt="image" src="https://github.com/user-attachments/assets/10e2f4c5-47f6-4005-8a96-8d1dd86437e5" />
<img width="817" height="635" alt="image" src="https://github.com/user-attachments/assets/6a21fe00-ec3f-4543-9c75-03f15c6e0d61" />
<img width="948" height="549" alt="image" src="https://github.com/user-attachments/assets/4ccaccfb-b84d-4373-9ca2-c7b52da157aa" />
<img width="827" height="644" alt="image" src="https://github.com/user-attachments/assets/2ba26bf0-5229-4c33-aca8-dd728e6a1b0f" />

* 參考來源： https://documentation.espressif.com/projects/esp-dev-kits/zh_CN/latest/esp32p4/esp32-p4-eye/user_guide.html?title=ESP32-P4-EYE%20%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97#getting-started



#### 上電

USB 接上電腦之後就會亮綠燈（右下角）
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/ed298e3f-2ba4-4b5d-92e1-fb6ed99f8549" />

#### 開機
* 鏡頭蓋要拿開
* 綠燈旁邊的IO開關，切換到I的位置
* 此時螢幕會點亮
* 此時為照相模式 Camera
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/493d99fa-4045-4be0-9397-54d34e6eb944" />

#### 模式切換
* 按壓 ▼ 右側的按鈕 可以依序切換模式

##### 定時拍照
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/95294982-624a-4847-8f4b-89c6faecd9d0" />

##### 錄影
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/58ecb843-b4af-466a-a70f-25d5f1faa995" />

##### 影像偵測
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/2c8e0cd2-8850-4f7a-88f1-0bac3bb4d068" />

* ◉ 右側按鈕按一下進入影像偵測模式
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/1cb4770c-8768-4ef8-84e1-37a125a920a9" />

* 快送滾動右上角的滾論 可以切換放大倍率 x1 x2 x3 x4

* 按壓 ▲▼ 右側的按鈕 可以依序切換偵測模式
  * 行人偵測
<img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/7f058f24-2085-48cd-8554-717fa577d078" />
  * 人臉偵測
 <img width="1477" height="1108" alt="image" src="https://github.com/user-attachments/assets/851146a4-608d-4706-8a82-63da5a93e4dd" />

* 如果無法偵測，請重新開機

## 期末評分
### 現有的範例
* https://github.com/espressif/esp-dev-kits.git
  * examples/esp32-p4-eye  

```
├── examples
│   ├── common_components
│   │   └── esp32_p4_eye
│   └── factory_demo
│       ├── 0004-fix-sdmmc-aligned-write-buffer.patch
│       ├── 0004-fix-spi-default-clock-source.patch
│       ├── CMakeLists.txt
│       ├── components
│       ├── main
│       ├── partitions.csv
│       ├── README_CN.md
│       ├── README.md
│       └── sdkconfig.defaults
```
### 評分方式
| 項目 | 分數 |
| --- | --- |
| 燒錄Factory範例PR | 60 |
| 更新模型成功（人臉->貓狗） | +10 |
| 完成更新模型操作PR | +10 | 
| 新增自訓練偵測模式 | +10 |
| 完成自訓練偵測模式 PR | +10 | 


## 軟體開發

ESP-EYE 可在 Linux、MacOs、Windows 作業系統中完成軟體燒寫。 目前，必須進行開發環境的工具鏈配置，詳見下方介紹。
<img width="512" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/4a687851-2312-4cd2-be3f-c022780da6b6">


### 準備工作
- 閱讀  https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32p4/get-started/index.html
- 閱讀 [ESP-IDF程式指南](https://espressif-docs.readthedocs-hosted.com/projects/esp-idf/zh-cn/latest/get-started/index.html)，參考對應章節，設定工具鏈；
- windows 可以使用 https://dl.espressif.com/dl/esp-idf/
- 準備 USB Type-C 線，用於連接 PC 和 ESP32-P4-EYE 開發板；
- 選擇適合開發環境的工具，例如 Terminal (Linux/MacOS) 或 MinGW (Windows) 等。
- AWS主控台登入
  - URL https://049281306005.signin.aws.amazon.com/console
  - 使用者名稱 class0@NTUT
### AWS Linux 範例
請使用這一區

<img width="331" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/7c7799d4-8784-418d-aafd-65d8c1684f92">

#### Launch SageMaker Notebook
* use "ml.c5.xlarge", that has 4 cpus
* 卷大小(以 GB 为单位) = 15GB
#### Setting Sagemaker Enviroment
* New a sagemaker terminal
* Change directory: for future file operation
```
cd SageMaker
```
* Installing new software on Amazon Linux, which is based on RHEL/CentOS, typically involves using the yum package manager (for Amazon Linux 2 and earlier
```
sudo yum update
sudo yum install ninja-build
```
cmake is already install , so we skip install cmake.
* mkdir esp for future working
```
mkdir esp
```
* clone source code
```
cd ./esp
git clone https://github.com/espressif/esp-dev-kits.git
git clone --recursive https://github.com/espressif/esp-idf.git
```

#### Local install
您需要在本機上安裝 ESP32 刷機工具。 ESP-IDF（物聯網開發框架）提供了 esptool.py，這是一個用於刷新 ESP32 裝置的 Python 實用程式。
如果您還沒有安裝 ESP-IDF 及其工具，可以使用 pip 單獨安裝 esptool.py：
```
pip install esptool
```

#### 使用 Minicom 来查看ESP32的输出
* 安装 Minicom
如果您还没有安装 Minicom，可以通过您的 Linux 发行版的包管理器进行安装。例如，在基于 Debian 的系统（如 Ubuntu）上，您可以使用以下命令安装：
```
sudo apt-get install minicom
```

对于 Amazon Linux 或基于 RHEL 的系统，使用：
```
sudo yum install minicom
```

对于 MacOS 的系统，使用：
```
brew install minicom
```


* 配置 Minicom
在启动 Minicom 之前，您需要知道您的设备连接到的串行端口号以及设备通讯的相关参数（如波特率）。通常，ESP32 等设备的默认波特率是 115200。

查找设备的串行端口：您可以使用 `dmesg | grep tty` 命令来查看设备连接的串行端口。通常，设备会被标记为 `/dev/ttyUSB0` 或 `/dev/ttyACM0`。MacOS 标记为 `/dev/tty.SLAB_USBtoUART` 或 `/dev/tty.usbmodem1101` `/dev/tty.usbmodem101` 後面數字隨機變動

* 配置 Minicom：运行 Minicom 的配置界面来设置串行端口参数。
```
sudo minicom -s
```
  * 在配置界面中，选择 "Serial port setup" 来设置串行端口参数。您需要设置以下几项：
    * Serial Device: 修改为您的设备串行端口，例如 /dev/ttyUSB0。
    * Bps/Par/Bits: 设置波特率（例如 115200）和其他通讯参数（通常为 8N1）。
    * Exit: 退出配置界面。
* 使用 Minicom 查看输出
配置完成后，您可以启动 Minicom 以连接到您的设备并查看输出（重新上電後）：

```
Welcome to minicom 2.10

OPTIONS:                                                                     
Compiled on Feb 22 2025, 10:10:35.                                           
Port /dev/tty.usbmodem1101, 10:49:58 [F]                                     
                                                                             
Press Meta-Z for help on special keys                                        
                                                                             
I (962) esp_image: segment 2: paddr=004f7bdc vaddr=4ff00000 size=0843ch ( 33852)d
I (971) esp_image: segment 3: paddr=00500020 vaddr=48000020 size=180d98h (157634p
I (1235) esp_image: segment 4: paddr=00680dc0 vaddr=4ff0843c size=12908h ( 76040d
I (1251) esp_image: segment 5: paddr=006936d0 vaddr=4ff1ad80 size=03d78h ( 15736d
I (1256) esp_image: segment 6: paddr=00697450 vaddr=50108080 size=0001ch (    28d
I (1263) boot: Loaded app from partition at offset 0x10000                   
I (1264) boot: Disabling RNG early entropy source...                         
I (1277) hex_psram: vendor id    : 0x0d (AP)                                 
I (1277) hex_psram: Latency      : 0x01 (Fixed)                              
I (1277) hex_psram: DriveStr.    : 0x00 (25 Ohm)                             
I (1278) hex_psram: dev id       : 0x03 (generation 4)                       
I (1283) hex_psram: density      : 0x07 (256 Mbit)                           
I (1287) hex_psram: good-die     : 0x06 (Pass)
I (1292) hex_psram: SRF          : 0x02 (Slow Refresh)                           
I (1296) hex_psram: BurstType    : 0x00 ( Wrap)                                  
I (1301) hex_psram: BurstLen     : 0x03 (2048 Byte)                              
I (1305) hex_psram: BitMode      : 0x01 (X16 Mode)                               
I (1310) hex_psram: Readlatency  : 0x04 (14 cycles@Fixed)                        
I (1315) hex_psram: DriveStrength: 0x00 (1/1)                                    
I (1319) MSPI DQS: tuning success, best phase id is 2                            
I (1502) MSPI DQS: tuning success, best delayline id is 10                       
I esp_psram: Found 32MB PSRAM device                                             
I esp_psram: Speed: 200MHz                                                       
I (1872) mmu_psram: .rodata xip on psram                                         
I (1989) mmu_psram: .text xip on psram                                           
I (1989) hex_psram: psram CS IO is dedicated                                     
I (1989) cpu_start: Multicore app                                                
I (2001) cpu_start: Pro cpu start user code                                      
I (2001) cpu_start: cpu freq: 360000000 Hz                                       
I (2001) app_init: Application information:                                      
I (2001) app_init: Project name:     factory_demo                                
I (2005) app_init: App version:      1.0.0                                       
I (2009) app_init: Compile time:     May 30 2025 17:39:07                        
I (2014) app_init: ELF file SHA256:  4cc7481a3...                                
I (2019) app_init: ESP-IDF:          v5.5-dev-2512-gfca19d0868f-dirt             
I (2025) efuse_init: Min chip rev:     v0.1                                      
I (2029) efuse_init: Max chip rev:     v1.99                                     
I (2033) efuse_init: Chip rev:         v1.3                                      
I (2037) heap_init: Initializing. RAM available for dynamic allocation:          
I (2043) heap_init: At 4FF23A70 len 00017550 (93 KiB): RAM                       
I (2048) heap_init: At 4FF3AFC0 len 00004BF0 (18 KiB): RAM                       
I (2053) heap_init: At 4FF40000 len 00040000 (256 KiB): RAM                      
I (2059) heap_init: At 5010809C len 00007F64 (31 KiB): RTCRAM                    
I (2064) heap_init: At 30100424 len 00001BDC (6 KiB): TCM                        
I (2069) esp_psram: Adding pool of 26112K of PSRAM memory to heap allocator      
I (2076) spi_flash: detected chip: generic                                       
I (2080) spi_flash: flash io: dio                                                
W (2083) bsp_p4_eye: Auto-initializing ESP32-P4-EYE board using constructor attre
I (2091) gpio: GPIO[46]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulld 
I (2099) gpio: GPIO[26]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulld 
I (2108) bsp_p4_eye: ESP32-P4-EYE board initialized successfully                 
I (2114) main_task: Started on CPU0                                              
I (2117) esp_psram: Reserving pool of 32K of internal memory for DMA/internal als
I (2125) main_task: Calling app_main()                                           
I (2128) main: Initialize NVS                                                    
I (2136) main: Initialize the flashlight                                         
I (2136) gpio: GPIO[23]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulld 
I (2143) main: Initialize the AI detect                                          
I (2146) app_ai_detect: Initialize the AI detect                                 
W (2151) FbsLoader: There is only one model in the flatbuffers, ignore the input!
W (2159) FbsLoader: CONFIG_SPIRAM_RODATA or CONFIG_SPIRAM_XIP_FROM_PSRAM option .
W (2236) FbsLoader: CONFIG_SPIRAM_RODATA or CONFIG_SPIRAM_XIP_FROM_PSRAM option .
W (2262) FbsLoader: CONFIG_SPIRAM_RODATA or CONFIG_SPIRAM_XIP_FROM_PSRAM option .
W (2273) FbsLoader: There is only one model in the flatbuffers, ignore the input!
W (2273) FbsLoader: CONFIG_SPIRAM_RODATA or CONFIG_SPIRAM_XIP_FROM_PSRAM option .
W (2868) dl::Model: Minimize() will delete variables not used in model inference.
I (2877) esp_painter: Painter initialized: 240x240, format: 0                    
I (2877) app_camera_pipeline: new elements[0]:0x48749508, internal:1             
I (2881) app_camera_pipeline: new elements[1]:0x4874b18c, internal:1             
I (2887) app_camera_pipeline: new elements[2]:0x4874ce10, internal:1             
I (2893) app_camera_pipeline: new elements[3]:0x4884863c, internal:1             
I (2900) app_camera_pipeline: new elements[4]:0x4884a2c0, internal:1             
I (2906) app_camera_pipeline: new pipeline 0x48750a7c, elem_num:5                
I (2911) app_camera_pipeline: new elements[0]:0x48750414, internal:1             
I (2918) app_camera_pipeline: new elements[1]:0x48750468, internal:1             
I (2924) app_camera_pipeline: new elements[2]:0x487507a8, internal:1             
I (2930) app_camera_pipeline: new elements[3]:0x487507fc, internal:1             
I (2936) app_camera_pipeline: new elements[4]:0x48750850, internal:1             
I (2942) app_camera_pipeline: new pipeline 0x48750b1c, elem_num:5                
I (2948) main: Initialize the display                                            
I (2951) LVGL: Starting LVGL task                                                
W (2954) p4-eye: If the pixel clock is not set to 20 MHz, you need to temporaril.
I (2972) gpio: GPIO[15]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulld 
I (3297) app_storage: Settings loaded from NVS successfully                      
I (3297) app_video_photo: Photo resolution set to 1920x1080                      
I (3297) app_video_record: Video resolution set to 1920x1080                     
I (3302) app_storage: Settings saved to NVS successfully                         
I (3307) app_storage: Settings saved to NVS successfully                         
I (3312) app_storage: Settings saved to NVS successfully                         
I (3317) app_storage: Camera settings loaded from NVS successfully               
I (3335) main: Initialize the storage                                            
I (3335) app_storage: other wake up                                              
I (3335) app_storage: Interval state loaded: active=0, next_wake=0               
I (3336) app_storage: Interval state saved: active=0, next_wake=0                
I (3342) app_storage: Photo count saved: 0                                       
I (3347) app_video_stream: Interval photo stopped                                
I (3350) app_storage: Photo count saved: 0                                       
I (3362) gpio: GPIO[45]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 0| Pulld 
I (3363) p4-eye: Setting LCD backlight: 100%                                     
I (3366) main: Initialize the application control module                         
I (3373) gpio: GPIO[2]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 0| Pulldo 
I (3380) gpio: GPIO[3]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 0| Pulldo 
I (3392) gpio: GPIO[4]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 0| Pulldo 
I (3397) gpio: GPIO[5]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 0| Pulldo 
I (3405) button: IoT Button Version: 3.5.0                                       
I (3409) gpio: GPIO[3]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldo 
I (3422) button: IoT Button Version: 3.5.0                                       
I (3422) gpio: GPIO[4]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldo 
I (3429) button: IoT Button Version: 3.5.0                                       
I (3433) gpio: GPIO[5]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldo 
I (3441) button: IoT Button Version: 3.5.0                                       
I (3452) gpio: GPIO[2]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldo 
I (3454) gpio: GPIO[48]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulld 
I (3463) gpio: GPIO[47]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulld 
I (3470) Knob: Iot Knob Config Succeed, encoder A:48, encoder B:47, direction:0,0
I (3482) main: Initialize the I2C                                                
W (3482) i2c.master: Please check pull-up resistances whether be connected propes
I (3497) main: Initialize the video streaming application                        
I (3504) ov2710: Detected Camera sensor PID=0x2710                               
I (3645) app_video: version: 0.9.0                                               
I (3645) app_video: driver:  MIPI-CSI                                            
I (3645) app_video: card:    MIPI-CSI                                            
I (3645) app_video: bus:     esp32p4:MIPI-CSI                                    
I (3648) app_video: width=1920 height=1080                                       
I (3652) app_storage: Camera settings loaded from NVS successfully               
I (3690) app_video_stream: Allocated shared photo buffer: 1843200 bytes (1280x72)
I (3693) app_ai_detect: AI detection buffers initialized successfully            
I (3698) app_storage: Photo count loaded: 0                                      
I (3698) app_storage: Photo count saved: 0                                       
I (3700) app_video_photo: Using shared photo buffer: 1843200 bytes               
I (3706) app_video_record: Using shared photo buffer: 1843200 bytes              
I (3712) p4-eye: bsp_microphone_init: 0                                          
W (3715) i2s_common: dma frame num is adjusted to 256 to align the dma buffer wi2
I (3725) I2S_IF: channel mode 1 bits:16/16 channel:2 mask:3                      
I (3730) Adev_Codec: Open codec device OK                                        
I (3733) app_video: Video Stream Start                                           
I (3739) main_task: Returned from app_main()                                     
I (7693) app_video_stream: Camera initialized after 50 frames                    

```



* 退出 Minicom
要退出 Minicom，您可以按 Ctrl-A 然后按 Z 键来进入 Minicom 的帮助菜单，再按 X 键退出。

### MacOS 範例
ESP-IDF 將使用 Mac OS 上預設安裝的 Python 版本。


安裝 pip:
```
brew install pip
```
安裝 pyserial:
```
pip install --user pyserial
```

安裝 CMake 和 Ninja 編譯工具：
```
brew install cmake ninja
```
強烈建議同時安裝 ccache 以獲得更快的編譯速度。 
```
brew install ccache
```
### CMake 介紹
 CMake是一個開源的跨平台自動化建置系統，它使用一個名為CMakeLists.txt的檔案來描述建置流程，可以產生標準的建置文件，例如Unix的Makefile或Windows的專案檔案。 以下是CMake的一些關鍵特性和基礎概念的簡介：

#### 關鍵特性
* 跨平台支援：CMake支援多種平台，包括但不限於Linux、macOS、Windows。
* 生成器：CMake可以產生多種編譯器和IDE的專案文件，如Makefile、Ninja、Visual Studio專案檔等。
* 可擴充：透過編寫模組和函數，可以擴展CMake的功能。
#### 基礎概念
* 變數：CMake中的變數用於儲存訊息，可以在CMakeLists.txt檔案中設定和引用。
* 指令：CMake腳本由一系列指令組成，每個指令代表一個操作，如設定變數、新增庫等。
* 目標：目標是建置過程中的關鍵概念，可以是執行檔、庫檔等。
* 屬性：目標、測試、目錄和全域等可以有屬性，屬性用來定義特定行為。
#### 開始使用
* 安裝CMake：首先，需要在你的系統上安裝CMake。
* 撰寫CMakeLists.txt檔案：這是CMake專案的核心文件，描述如何建構專案。
* 設定專案：使用cmake命令列工具對專案進行配置，產生建置檔。
* 建置專案：透過產生的建置檔案（如Makefile）建置專案。

### Ninja  介紹
是一個緊湊且快速的建置系統，旨在盡快處理專案建置。 與許多傳統的建置系統不同，Ninja 以其簡單性和高效性而著稱，使其成為需要快速迭代周期的大型專案的首選。 以下介紹了 Ninja 的脫穎而出之處：

#### 主要特徵：
* 速度：忍者註重速度。 它透過避免不必要的工作並優化增量建置的建置過程來實現這一點。
* 簡單性：雖然 Ninja 建立檔案是人類可讀的，但它們並不適合手寫。 相反，它們是由 CMake 等更高層級的建置系統產生的，提供簡單且高效的工作流程（Ninja Build）。
#### 何時使用Ninja：
* Ninja 本身並不是一個成熟的建造系統，而是被設計為用作更大的建造系統的一部分。 它對於需要最小化建置時間的專案特別有益，例如 Google Chrome 和 Android 的一部分（Ninja Build）。
* 對於需要快速、可靠且最小設定來編譯程式碼的開發人員來說，它是理想的選擇（Ninja Build）。
#### Ninja的工作原理：
* Ninja 建構在 build.ninja 檔案中進行描述，其中包括檔案應如何編譯的規則以及檔案之間的依賴關係（CnBlogs）。
* 它使用簡單的語法來定義建置規則和依賴項，從而最佳化增量建置。 當檔案變更時，Ninja 僅重建受該變更影響的專案部分（CnBlogs）（維基百科）。
#### Ninja入門：
* 安裝：Ninja 可以使用macOS 上的Homebrew（brew install ninja）、Windows 上的Chocolatey（choco install ninja）等套件管理器進行安裝，或者透過Conda 和Pip（Earthly - 讓建置超級簡單）等其他套件管理器進行安裝。
* 建立您的第一個專案：要使用 Ninja 建置項目，您通常需要 CMake 等更高層級的建置系統來產生 build.ninja 檔案。 檔案產生後，您可以執行 Ninja 來編譯專案（Earthly - 讓建置超級簡單）。
#### 增量構建：
* Ninja 擅長增量構建，僅重新編譯更改的文件，從而大大縮短大型專案的構建時間（Earthly - 讓構建超級簡單）。
* 典型的工作流程包括使用 CMake (cmake -G Ninja ..) 產生 Ninja 建置文件，然後執行 Ninja 來建置專案 (ninja)。 這個過程很簡單，可以顯著加快開發週期（Earthly - 讓建置超級簡單）。

### Project Building Hands on 
Creating a "Hellow world" example
* 切換到名為 esp 的目錄：
```
cd esp
```
* 遞歸克隆 esp-who 專案的 Git 儲存庫：
```
git clone --recursive https://github.com/espressif/esp-who.git
```
* 遞歸克隆 esp-idf 專案的 Git 儲存庫：
```
git clone --recursive https://github.com/espressif/esp-idf.git
```
* 切換到 esp-idf 目錄：
```
cd esp-idf/
```
* 執行 install.sh 腳本，安裝開發環境：
```
./install.sh
```
* 執行 export.sh 腳本，設置環境變量：
```
source ./export.sh
```
* 返回上一級目錄：
```
cd ..
```

* 從 IDF_PATH 環境變量指定的路徑復制 hello_world 範例到當前目錄：
```
cp -r $IDF_PATH/examples/get-started/hello_world .
```
* 切換到 hello_world 目錄：
```
cd hello_world/
```

* 執行 idf.py 工具進行配置（例如設置項目參數）：
```
idf.py set-target esp32s3
idf.py menuconfig
```
<img width="513" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/cd5da1d0-5404-4e36-82f2-ad104b90d7fe">

* 使用 idf.py 工具構建項目：
```
idf.py fullclean
idf.py build
```
注意構建後的燒錄指令

<img width="1133" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/65dba0ad-f191-46ef-8665-6b4b2c273061">


### Image Flashing Hands on 
要把 AWS 云上的 Amazon Linux 环境中构建的 ESP32 项目烧录到您本地的设备上，您需要通过以下几个步骤操作：
#### 下载构建结果
* 将构建好的固件（通常是 .bin 文件）从您的云服务器下载到您的本地计算机。您可以使用 SageMaker Download 。有三個檔案要下載
  *  build/partition_table/partition-table.bin 
  *  build/bootloader/bootloader.bin
  *  build/hello_world.bin
* 例如，選取路徑如下：

<img width="362" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/10518230-f321-413f-aa3b-3fb3a2dd2cdf">

* 選擇檔案

<img width="268" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/2f3f6977-1953-481a-adb5-c98d29adcb55">

* 點選Download

<img width="133" alt="image" src="https://github.com/itemhsu/AIoT_one/assets/25599185/58bddf32-afad-46f9-95c9-8867fd9aecd9">

#### 燒錄韌體

* 使用 ESP-IDF 提供的燒錄工具將下載的韌體燒錄到您的裝置上。 esp32燒錄指令可能看起來像這樣：
  
```
esptool.py --chip esp32 -p /dev/tty.SLAB_USBtoUART  write_flash -z 0x1000 ./bootloader.bin 0x8000 ./partition-table.bin  0x10000 ./hello_world.bin
```
* esp32s3 燒錄指令可能看起來像這樣：
```
esptool.py --chip esp32s3 -p /dev/tty.usbmodem11301 erase_flash
esptool.py --chip esp32s3 -p /dev/tty.usbmodem11301 -b 460800 --before default_reset --after hard_reset write_flash --flash_mode dio --flash_size 4MB --flash_freq 40m 0x0 bootloader.bin 0x8000 partition-table.bin 0x10000 hello_world.bin
```
linux 
```
esptool.py --chip esp32s3 -p /dev/ttyACM0 erase_flash
esptool.py --chip esp32s3 -p /dev/ttyACM0 -b 460800 --before default_reset --after hard_reset write_flash --flash_mode dio --flash_size 4MB --flash_freq 40m 0x0 bootloader.bin 0x8000 partition-table.bin 0x10000 hello_world.bin

```
#### 執行結果（minicom）
```
rst:0xc (SW_CPU_RESET),boot:0x13 (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:2
load:0x3fff0030,len:7176
load:0x40078000,len:15564
ho 0 tail 12 room 4
load:0x40080400,len:4
load:0x40080404,len:3904
entry 0x40080640
I (31) boot: ESP-IDF v5.3-dev-3220-g9c99a385ad 2nd stage bootloader
I (31) boot: compile time Apr  5 2024 08:51:47
I (33) boot: Multicore bootloader
I (37) boot: chip revision: v1.0
I (41) boot.esp32: SPI Speed      : 40MHz
I (45) boot.esp32: SPI Mode       : DIO
I (50) boot.esp32: SPI Flash Size : 2MB
I (54) boot: Enabling RNG early entropy source...
I (60) boot: Partition Table:
I (63) boot: ## Label            Usage          Type ST Offset   Length
I (71) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (78) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (86) boot:  2 factory          factory app      00 00 00010000 00100000
I (93) boot: End of partition table
I (97) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=09414h ( 37908) map
I (119) esp_image: segment 1: paddr=0001943c vaddr=3ffb0000 size=02200h (  8704) load
I (122) esp_image: segment 2: paddr=0001b644 vaddr=40080000 size=049d4h ( 18900) load
I (132) esp_image: segment 3: paddr=00020020 vaddr=400d0020 size=13850h ( 79952) map
I (161) esp_image: segment 4: paddr=00033878 vaddr=400849d4 size=077ech ( 30700) load
I (179) boot: Loaded app from partition at offset 0x10000
I (179) boot: Disabling RNG early entropy source...
I (191) cpu_start: Multicore app
I (199) cpu_start: Pro cpu start user code
I (199) cpu_start: cpu freq: 160000000 Hz
I (200) app_init: Application information:
I (202) app_init: Project name:     hello_world
I (208) app_init: App version:      1
I (212) app_init: Compile time:     Apr  5 2024 08:52:04
I (218) app_init: ELF file SHA256:  bb6384479...
I (223) app_init: ESP-IDF:          v5.3-dev-3220-g9c99a385ad
I (230) efuse_init: Min chip rev:     v0.0
I (234) efuse_init: Max chip rev:     v3.99
I (239) efuse_init: Chip rev:         v1.0
I (245) heap_init: Initializing. RAM available for dynamic allocation:
I (252) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (258) heap_init: At 3FFB2AC8 len 0002D538 (181 KiB): DRAM
I (264) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (270) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (277) heap_init: At 4008C1C0 len 00013E40 (79 KiB): IRAM
I (284) spi_flash: detected chip: generic
I (287) spi_flash: flash io: dio
W (291) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the.
I (305) main_task: Started on CPU0
I (315) main_task: Calling app_main()
Hello world!
This is esp32 chip with 2 CPU core(s), WiFi/BTBLE, silicon revision v1.0, 2MB external flash
Minimum free heap size: 305360 bytes
Restarting in 10 seconds...
Restarting in 9 seconds...
Restarting in 8 seconds...
Restarting in 7 seconds...
Restarting in 6 seconds...
Restarting in 5 seconds...
Restarting in 4 seconds...
Restarting in 3 seconds...
Restarting in 2 seconds...
Restarting in 1 seconds...
Restarting in 0 seconds...
Restarting now.
ets Jun  8 2016 00:22:57
```
#### hello_world_main.c
```c
/*
 * SPDX-FileCopyrightText: 2010-2022 Espressif Systems (Shanghai) CO LTD
 *
 * SPDX-License-Identifier: CC0-1.0
 */

#include <stdio.h>
#include <inttypes.h>
#include "sdkconfig.h"
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_chip_info.h"
#include "esp_flash.h"
#include "esp_system.h"

void app_main(void)
{
    printf("Hello world!\n");

    /* Print chip information */
    esp_chip_info_t chip_info;
    uint32_t flash_size;
    esp_chip_info(&chip_info);
    printf("This is %s chip with %d CPU core(s), %s%s%s%s, ",
           CONFIG_IDF_TARGET,
           chip_info.cores,
           (chip_info.features & CHIP_FEATURE_WIFI_BGN) ? "WiFi/" : "",
           (chip_info.features & CHIP_FEATURE_BT) ? "BT" : "",
           (chip_info.features & CHIP_FEATURE_BLE) ? "BLE" : "",
           (chip_info.features & CHIP_FEATURE_IEEE802154) ? ", 802.15.4 (Zigbee/Thread)" : "");

    unsigned major_rev = chip_info.revision / 100;
    unsigned minor_rev = chip_info.revision % 100;
    printf("silicon revision v%d.%d, ", major_rev, minor_rev);
    if(esp_flash_get_size(NULL, &flash_size) != ESP_OK) {
        printf("Get flash size failed");
        return;
    }

    printf("%" PRIu32 "MB %s flash\n", flash_size / (uint32_t)(1024 * 1024),
           (chip_info.features & CHIP_FEATURE_EMB_FLASH) ? "embedded" : "external");

    printf("Minimum free heap size: %" PRIu32 " bytes\n", esp_get_minimum_free_heap_size());

    for (int i = 10; i >= 0; i--) {
        printf("Restarting in %d seconds...\n", i);
        vTaskDelay(1000 / portTICK_PERIOD_MS);
    }
    printf("Restarting now.\n");
    fflush(stdout);
    esp_restart();
}
```
