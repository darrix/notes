# Typescript notes

## Jesse Liberty on LinkedIn

### Types in typescript

*var* variables are scoped to the surrounding block, i.e., globally.  Instead, use *let* and *const*, which are scoped to the current block

## How to enable Build routines in VSCode

You can use Ctrl+Shift+B to start a build of a TS application.  There are two versions TSC Build and TSC Watch.  Build will transpile on command, while Watch will look for changes in the source files and run as required.

## Creating a simple project

There's a simple BabylonJS project that draws a ball in a browser.  You can create the HTML for it with the following frame

```html
/// <reference path="../node_modules/babylonjs/babylon.d.ts" />

var canvas =  document.getElementById("renderCanvas") as HTMLCanvasElement;

var engine = new BABYLON.Engine(canvas, true);

var createScene = function () : BABYLON.Scene 
{
    var scene = new BABYLON.Scene(engine);
    var camera = new BABYLON.ArcRotateCamera("Camera", Math.PI / 2, Math.PI / 2, 2, BABYLON.Vector3.Zero(), scene);
    camera.attachControl(canvas, true);
    var light1 = new BABYLON.HemisphericLight("light1", new BABYLON.Vector3(1, 1, 0), scene);
    var light2 = new BABYLON.PointLight("light2", new BABYLON.Vector3(0,1,-1), scene);
    var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", { diameter:2}, scene);
    return scene;

}

var scene = createScene();

engine.runRenderLoop( () => scene.render() );

window.addEventListener("resize", function () { scene.render(); });
```
Along with that, you need JavaScript.  The original JS is as follows:
```javascript

            var canvas = document.getElementById("renderCanvas"); // Get the canvas element 

            var engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine


            /******* Add the create scene function ******/
            var createScene = function () {

                        // Create the scene space
                        var scene = new BABYLON.Scene(engine);

                        // Add a camera to the scene and attach it to the canvas
                        var camera = new BABYLON.ArcRotateCamera("Camera", Math.PI / 2, Math.PI / 2, 2, BABYLON.Vector3.Zero(), scene);
                        camera.attachControl(canvas, true);

                        // Add lights to the scene
                        var light1 = new BABYLON.HemisphericLight("light1", new BABYLON.Vector3(1, 1, 0), scene);
                        var light2 = new BABYLON.PointLight("light2", new BABYLON.Vector3(0, 1, -1), scene);


                        // Add and manipulate meshes in the scene
                        var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", {diameter:2}, scene);

                        return scene;
                };

                /******* End of the create scene function ******/    

                var scene = createScene(); //Call the createScene function

            engine.runRenderLoop(function () { // Register a render loop to repeatedly render the scene
                    scene.render();
            });


            window.addEventListener("resize", function () { // Watch for browser/canvas resize events
                    engine.resize();
            });
```
This can be changed minimally for Typescript by accessing the type definition file from Babylon.

```typescript
/// <reference path="../node_modules/babylonjs/babylon.d.ts" />

var canvas =  document.getElementById("renderCanvas") as HTMLCanvasElement;

var engine = new BABYLON.Engine(canvas, true);

var createScene = function () : BABYLON.Scene 
{
    var scene = new BABYLON.Scene(engine);
    var camera = new BABYLON.ArcRotateCamera("Camera", Math.PI / 2, Math.PI / 2, 2, BABYLON.Vector3.Zero(), scene);
    camera.attachControl(canvas, true);
    var light1 = new BABYLON.HemisphericLight("light1", new BABYLON.Vector3(1, 1, 0), scene);
    var light2 = new BABYLON.PointLight("light2", new BABYLON.Vector3(0,1,-1), scene);
    var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", { diameter:2}, scene);
    return scene;

}

var scene = createScene();

engine.runRenderLoop( () => scene.render() );

window.addEventListener("resize", function () { scene.render(); });

(* 
Note that another way to write that last line is to say
window.addEventListener("resize", () => scene.render()); //function () { scene.render(); });

*)
```


So. let's create a fable instance and add babylonjs to that.

```
dotnet new fable -n bblyfbl -lang F#
cd bblyfbl
npm install babylonjs
```
If we look at 
