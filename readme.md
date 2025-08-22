# build-sfml-imgui

Simple program to show how to build project with SFML and ImGui-SFML (static linking only)

## Steps for building library

1. Create a directory `build` in root directory
2. Open terminal and run the following command
3. Change directory to `build`
4. Run the following commands to set up `build` directory
   1. for `Visual Studio 17 2022` build <br>
      run `cmake --preset vs ..`
   2. for `Unix Makefiles` build <br>
      run `cmake --preset make ..`
5. for building the project:
   1. for `Visual Studio 17 2022` build <br>
      run `./build-sfml-imgui.sln`
   2. for `Unix Makefiles` build <br>
      run `make build-sfml-imgui`
6. For running the project:
   1. for `Visual Studio 17 2022` build <br>
      use visual studio to run the project
   2. for `Unix Makefiles` build <br>
      run `./build-sfml-imgui`
