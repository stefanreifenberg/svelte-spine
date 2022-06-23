# Import a Spline scene directly from [spline.design](https://spline.design/).

Spline makes it easy to create a scene with all kinds of 3d elements. There are various option for exporting the scene. Basically what you need to do is select Code and then Three.js. 
The most important part of the code is this part:
```
const loader = new SplineLoader();
loader.load(
  'https://prod.spline.design/bPyo53wTrYqJgajV/scene.splinecode',
  (splineScene) => {
    scene.add(splineScene);
  }
);
```
In order to use this in Svelte all we need to do is modify the scene.add and replace it with this:
```
let model;

// import spline scene
const loader = new SplineLoader();

onMount(() => {
  loader.load(
    'https://prod.spline.design/6ZQA4GzzFjXNeDE4/scene.splinecode',
    (splineScene) => {
    model = splineScene;
  });
});
```
The here called "model" can then be used inside an SC.Primitive.
```
<SC.Primitive
    object={model}
    scale={[1, 1, 1]}
    position={[0, 0, 0]}
    rotation={[0, 0, 0]}
  />
```
And that's it.
Check the App.svelte in this repo for the full code.
Cheers!
