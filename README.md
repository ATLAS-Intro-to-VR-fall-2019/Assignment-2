# Assignment-2: Your First VR App

## Setting Up the Environment
First let's get Unity ready to deploy Google Cardboard VR for our phones. Once you have gone through the same steps you used to deploy to your device from Assignment one follow the corresponding quickstart guide for your platform
- [Android](https://developers.google.com/vr/develop/unity/get-started-android)
- [IOS]()

Unity supports Google Cardboard and a few other headsets out of the box, it will automatically calculate the rotation based on the accelerometer in your device and render two camera views of the same scene. Try adding some elements to the scene so it's easier to orient yourself in VR.

## Adding Some Interaction
First let's make it so we can move around in VR. A simple one would be, when we touch the screen, move forward in the direction we are touching. To accomplish this we must apply the *Forward Vector* of the camera to it's *transform*. Let's create a new script called *CameraMovement* and add it to the Main Camera in our scene. The inside of your CameraMovement class should look like this
```
bool isTouchDown = false;
Vector3 speed = new Vector3(0.3f, 0.3f, 0.3f);

void Update() {
    // Set our touch down variable
    if (Input.GetMouseButtonDown(0)) isTouchDown = true;
    if (Input.GetMouseButtonUp(0)) isTouchDown = false;

    if (Input.GetMouseButtonDown(0)) {
        // Calculate the movement using our speed and the forward of our camera
        // The forward is a Unit Vector (magnitude of 1)
        // which points in the direction our camera is looking
        Vector3 moveVec = Vector3.Scale(transform.forward, speed);
        transform.position = transform.position + moveVec;
    }
}
```
Now when you tap the screen, the camera should move forward through the space.

## Raycast Target Practice
First, disable your *CameraMovement* script by removing the component from the GameObject in the inspector. Then Create a 3D shape (any one you prefer, I chose a sphere) and name it Target, we will be using this as our Prefab for targets. Before we turn it into a prefab though, we need to give it a Layer. In Unity when we want to detect collisions or raycasting, we can assign objects layers so that we can limit the scope of what we are checking for collisions with. To add a new layer click the *Layer* field at the top of the Target GameObject in the Inspector and select the option *Add New Layer*, and name the 8th slot `Targets`. Then select the Target for inspection again, and set the layer property to Targets. Now drag Target into the project area to turn it into a prefab, and delete it from the scene.

If you have never heard of Raycasting before, think of it simply as shooting out a line (ray) into the world to see if it collides with anything. This can be incredibly useful for 3D applications, in our case we are going to use raycasting to determine if the player is looking directly at the target. To implement raycasting we will need a new script, create one called *RaycastToTarget*, then open it in your editor. First let's add a private property for the layer target
```
private int targetLayer = 1 << 8; // Layer 8 (environment)
```

## Assignment Turn In
Zip up your code and submit it on canvas. In addition demonstrate the functioning app before the deadline to the instructor.

## Bonus
Complete any of the following for up to a total of 3 Bonus points on this assignment
- Create a Game Object with a script that will randomly spawn the target prefab over time **1 pt**
- Make it so that when the targets are clicked, instead of being deleted they change shape **0.5 pt**
- Combine the moving and raycast scripts so that when you are not pointing at a target, you move forward **0.5 pt**
- Instead of moving forward, make it so you can look at the ground and teleport to that spot when you click **1 pt**
