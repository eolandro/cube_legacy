# cube_legacy

This is a cube engine repo, but has been improved for compilation in modern systems

 **No windows Support** (because i have no windows)

## How to compile

Like original cube engine, you need both runtime and developer package: **SDL1**, **SDL1_image**, **SDL1_mixer**, **GLUT library**, **zlib** and **X11**. In addition developer tools: **cmake 3.18+**, **gcc/clang** and **make** are necessary.

### GNU/Linux

On Distros like **Debian**

`$sudo apt install build-essential cmake git libsdl1.2debian  libsdl1.2-dev libsdl-mixer1.2-dev libsdl-mixer1.2 libsdl-image1.2 libsdl-image1.2-dev freeglut3 freeglut3-dev x11proto-dev zlib1g-dev zlib1g`

Clone the this repo:

`$git clone https://github.com/eolandro/cube_legacy.git`

Change to repo and create dir *build*

`$cd cube_legacy`

`$mkdir build`

Invoke cmake and make

`$cmake ..`

`$make`

you will get **cube_client** and **cube_server**

### Termux

Even it is a work in progress... It's possible to compile and run cube legacy in termux.

1. First you need X11.
   `pkg update`
   `pkg install x11-repo``

2. Now you need a vnc server (yes it works with vncserver)
   `pkg install tigervnc``

3. Desktop environment. At this time fluxbox
   `pkg install fluxbox`

4. (optional) fluxbox can be started automatically on VNC server startup. To do this, edit file `~/.vnc/xstartup` as shown here:
   
   ```
   #!/data/data/com.termux/files/usr/bin/sh
   
   ## Fluxbox desktop.
   
   # Generate menu.
   
   fluxbox-generate_menu
   
   # Start fluxbox.
   
   fluxbox &
   ```

5. Install cube dependencies
   `pkg install build-essential libx11 libx11-static sdl sdl-image-static sdl-mixer sdl-mixer-static zlib-static zlib virglrenderer-android mesa mesa-dev cmake git `

6. Clone the this repo:
   
   `$git clone https://github.com/eolandro/cube_legacy.git`

7. Change to repo and create dir *build*
   
   `$cd cube_legacy`
   
   `$mkdir build`

8. Invoke cmake and make
   
   `$cmake ..`
   
   `$make`

9. you will get **cube_client** and **cube_server** 

10. Get vnc client. I recommend [MultiVNC | F-Droid - Free and Open Source Android App Repository](https://f-droid.org/es/packages/com.coboltforge.dontmind.multivnc/)

## How to run cube_legacy

1. You need the original cube package *cube_2005_08_29_unix.tar.gz* from sourceforge [Cube game &amp; 3D engine - Browse /cube/2005_08_29 at SourceForge.net](https://sourceforge.net/projects/cube/files/cube/2005_08_29/)

2. Decompress *cube_2005_08_29_unix.tar.gz*,
   `tar -xf cube_2005_08_29_unix.tar.gz cube/`

3.  Put **cube_client** and **cube_server** in the new cube directorory

4. Run ./cube_client in cube directory
