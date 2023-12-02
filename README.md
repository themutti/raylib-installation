# Installing and compiling raylib

[Raylib](https://www.raylib.com/) is an open-source game development library written in c that allows you to create 2D and 3D games and any kind of application.

This guide will help you setup and compile your first project in Raylib.


## Installation

To get started, install the latest version of Raylib locally by cloning the [repository](https://github.com/raysan5/raylib):

```bash
git clone --depth=1 https://github.com/raysan5/raylib
```

Ensure you also have `Make` installed.


## Setup a project

1. Create a new directory for your project.

2. Inside your project directory, create two folders: `include` and `lib`.

3. Go to where you previously installed Raylib and navigate to the `raylib/src/` folder.

4. Copy the `raylib.h` file to your project's `include` folder.

5. Compile the library:

    ```bash
    mingw32-make PLATFORM=PLATFORM_DESKTOP
    ```

    *Note: Specify the target platform accordingly.*

6. The previous command generated a `libraylib.a` file. Copy it to the `lib` folder in your project.

7. Create a `main.c` file where you can include Raylib and start developing your game:

    ```c
    #include "raylib.h"

    int main() {
      const int screenWidth = 800;
      const int screenHeight = 600;
      InitWindow(screenWidth, screenHeight, "Raylib basic window");
      SetTargetFPS(60);
      while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("It works!", 20, 20, 20, BLACK);
        EndDrawing();
      }
      CloseWindow();
      return 0;
    }
    ```

---

At the end, your project should look something like this:

```
your-raylib-project
│
├─── include
│    └─── raylib.h
│
├─── lib
│    └─── libraylib.a
│
└─── main.c
```


## Compile the project

To compile your project and generate an executable file, all you need to do is run this command:

```bash
gcc main.c -o app.exe -O1 -Wall -std=c99 -Wno-missing-braces -I ./include/ -L ./lib/ -lraylib -lopengl32 -lgdi32 -lwinmm
```

*Note: Adjust the executable name as desired with the `-o` option.*

And that's it. You have successfully created and compiled your first Raylib project!
