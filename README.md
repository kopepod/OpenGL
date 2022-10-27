# OpenGL

This is a tutorial to install and run OpenGL for Linux. Steps:

1. Install OpenGL
2. Install VSCode
3. Create a project
4. Run from VSCode

## 1. Install OpenGL dependencies

```
sudo apt-get update  
sudo apt-get install freeglut3 -y
sudo apt-get install freeglut3-dev -y 
sudo apt-get install binutils-gold -y 
sudo apt-get install g++ cmake -y 
sudo apt-get install libglew-dev -y 
sudo apt-get install g++ -y 
sudo apt-get install mesa-common-dev -y 
sudo apt-get install build-essential -y 
sudo apt-get install libglew1.5-dev libglm-dev -y 
```

## 2. Install VSCode

Download from here https://code.visualstudio.com/download

```
sudo dpkg -i codeXXXX.deb
```

## 3. Create a project
* Files
```
mkdir NewProject
cd NewProject
code .
nano Main.c
```
* Code: 
- Copy-paste into a new Main.cpp file
- 
```
#include <GL/glut.h>

void displayMe(void)
{
    glClear(GL_COLOR_BUFFER_BIT);
    glBegin(GL_POLYGON);
        glVertex3f(0.5, 0.0, 0.5);
        glVertex3f(0.5, 0.0, 0.0);
        glVertex3f(0.0, 0.5, 0.0);
        glVertex3f(0.0, 0.0, 0.5);
    glEnd();
    glFlush();
}

int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE);
    glutInitWindowSize(400, 300);
    glutInitWindowPosition(100, 100);
    glutCreateWindow("Hello world!");
    glutDisplayFunc(displayMe);
    glutMainLoop();
    return 0;
}
```
* Compile from terminal
```
$ g++ Main.cpp -o runme -lglut -lGLU -lGL
```
* Run from terminal
```
$ ./runme
```
## 4. Run from VSCode

- Click Extensions (Ctrl+Shift+x)
- Install C/C++ and C/C++ Extension Pack
- Run (F5)
- Create a _launch.json_ file

```
{
// launch.json
    "version": "0.2.0",
    "configurations": [
        {
            "name": "C/C++: gcc build and debug active file",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}/${fileBasenameNoExtension}",
            "args": [
                "-lGL","-lGLU","-lglut"
            ],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "Set Disassembly Flavor to Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "C/C++: gcc build active file",
            "miDebuggerPath": "/usr/bin/gdb"
        }
    ]
}
```



