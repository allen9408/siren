# 音频编码工具配置


## 1. PJmedia setup

### Support targets
 - Linux
 - MACOS X (to be verified)

---

### Requirements
1. GNU make
2. GNU binutils for the target
3. GNU gcc

---

### Video support
1. linux: v4l2 development library
    `sudo apt-get install libv4l-dev`

2. SDL **version 2.0**
    http://www.libsdl.org/download-2.0.php

3. ffmpeg
    http://ffmpeg.org/download.html

---

### Running configure
1. Enable G722.1:
> pjpeoject/pjmedia/include/pjmedia-codec/congif.h: line 312  
    DEFINE PJMEDIA\_HAS\_G7221\_CODEC    **0 -> 1**

2. Configure and make

    `./configure  `  
    `make dep  `  
    `make  `  
    `sudo make install`  

---

## 2. Build app
- Create a directory outside the PJSIP sources for your project and place your source files there. 
- Create Makefile (<font color=red >**!!!Change spaces into tab**</font>)
> \# If your application is in a file named myapp.cpp or myapp.c  
> \# this is the line you will need to build the binary.  
all: myapp  
> myapp: myapp.cpp  
> &#160; &#160; &#160; &#160;$(CC) -o $@ $< \`pkg-config --cflags --libs libpjproject\`  
> clean:  
> &#160; &#160; &#160; &#160;rm -f myapp.o myapp  

- Add app(myapp.c) in directory
- run **make**

---

## 3. notes
- Samples directory:
> pjproject/pjsip-apps/src/samples/

- Official Document: `http://www.pjsip.org/docs/latest/pjmedia/docs/html/index.htm`

- G722.1 Codec: `http://www.pjsip.org/pjmedia/docs/html/group__PJMED__G7221__CODEC.htm`

- Run siren: `./siren input.wav output.wav`
    