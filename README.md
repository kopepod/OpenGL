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

## Create a project
* Files
```
mkdir NewProject
cd NewProject
code .
nano Main.c
```
* Code
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
* Compile
```
$ g++ Main.cpp -o runme -lglut -lGLU -lGL
```
* Run
```
$ ./runme
```
