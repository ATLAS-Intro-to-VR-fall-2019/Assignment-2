# Assignment-2: Your First VR App

## Setting Up the Environment
First let's get Unity ready to deploy Google Cardboard VR for our phones. Once you have gone through the same steps you used to deploy to your device from Assignment one follow the corresponding quickstart guide for your platform
- [Android](https://developers.google.com/vr/develop/unity/get-started-android)
- [IOS]()

Unity supports Google Cardboard and a few other headsets out of the box, it will automatically calculate the rotation based on the accelerometer in your device and render two camera views of the same scene. Try adding some elements to the scene so it's easier to orient yourself in VR.

## Adding Some Interaction
First let's make it so we can move around in VR. A simple one would be, when we touch the screen, move forward in the direction we are touching. To accomplish this we must apply the *Forward Vector* of the camera to it's *transform*. Let's create a new script called *CameraMovement* and add it to the Main Camera in our scene.

In the `update` function of the *CameraMovement* script, let's add our touch code from last time 

## Raycast Target Practice
target prefab
raycast

## Assignment Turn In
Zip up your code and submit it on canvas. In addition demonstrate the functioning app before the deadline to the instructor.

## Bonus
Complete any of the following for up to a total of 3 Bonus points on this assignment

- Create a Game Object with a script that will randomly spawn the target prefab over time **1 pt**
- Make it so that when the targets are clicked, instead deleted they change shape **0.5 pt**
- Instead of moving forward, make it so you can look at the ground and teleport to that spot when you click **1.5 pt**
