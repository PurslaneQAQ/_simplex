# Compile and run the sample code
Check the sample projects under /proj. For the first step, you need to build /proj/_install to generate .lib files for all the external and internal libraries.

#### Build precompiled libraries on Windows:
**Notice, on Windows, using Cmake in cmd line may causes a compile error after generating the VS project. So the Cmake GUI is recommended.**

1. Open Cmake GUI.

<img width="30%" height="30%" src="._static/make_guide/0.png"/>

2. Add source code `[Your path]/simplex/proj/_install` and build `[Your path]/simplex/build/_install/cmake-build-win`.

<img width="70%" height="70%" src="._static/make_guide/1.png"/>

3. Click on the left bottom button `Configure`. Specify the generator for this project as `Visual Studio 15 2017 Win64`. 

<img width="70%" height="70%" src="._static/make_guide/2.png"/>

4. Click on the next button `Generate`.

<img width="70%" height="70%" src="._static/make_guide/3.png"/>

5. Click on the next button `Open_Project` to open Visual Studio.

<img width="70%" height="70%" src="._static/make_guide/4.png"/>

6. Compile the code in VS with Release, x64. Build.

<img width="70%" height="70%" src="._static/make_guide/5.png"/>

#### Build precompiled libraries on Linux:

1. Create a build folder: `[Your path]/simplex/build/_install/cmake-build-unix`

2. cd to the build folder and run CMake with specified source code path: `[Your path]/simplex/proj/_install`.

2. In the same folder, run `make` to compile.

3. Repeat step 1-2 for fluid\_euler and opengl\_viewer.

Once successfully building the library, you should be able to see the compiled libraries in lib/ext and lib/slax.

#### Build the OpenGL Viewer:
1. Repeat step 1-6 for proj/opengl\_viewer. After successful build, you should be able to find the opengl_viewer.exe in bin/win/opengl_viewer/Release/opengl_viewer.exe
2. Set the executable as a environment variable 'o'.

<img width="70%" height="70%" src="._static/make_guide/6.png"/>
<img width="70%" height="70%" src="._static/make_guide/7.png"/>

#### Build and run the fluid euler project:

1. Build the proj/fluid_euler project as abo e.

2. In `[Your path]/simplex/bin/win/fluid_euler/Release`, run command: 

        fluid_euler.exe -test 3 -s 64 -lf 200 -o water
    
    Arguments:
    -test: 3, droplet falling into water; 4. droplet oscillation with surface tension
    -s: resolution
    -lf: last frame
    -o: output folder

2. Visualize the result with the opengl viewer: 
copy `opengl_viewer.exe` and its dlls in `ext/_dll` to the same folder as fluid_euler.exe, run command 

        opengl_viewer.exe -m fluid -o water
Or, if you have set the environmental variable, use:
    %o% -m fluid -o water

    Keyboard shortcuts:
    `p`: play/stop the animation
    `[` `]`: next / previous frame
    `v`: turn on/off velocity
    `g`: turn on/off grid
    `l`: turn on/off levelset field
    `w`: offscreen rendering