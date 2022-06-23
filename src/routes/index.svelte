<script lang="ts">
	import BABYLON from 'babylonjs';

	let canvas = document.getElementById('canvas') as HTMLCanvasElement;

	const createScene = () => {
		let engine: BABYLON.Engine = new BABYLON.Engine(canvas);

		let scene: BABYLON.Scene = new BABYLON.Scene(engine);

		let camera: BABYLON.Camera = new BABYLON.FreeCamera(
			'camera',
			new BABYLON.Vector3(0, 7, -9),
			scene
		);

		camera.attachControl(canvas, false);
		let light: BABYLON.Light = new BABYLON.HemisphericLight(
			'light',
			new BABYLON.Vector3(0, 1, 1.5),
			scene
		);

		light.intensity = 0.6;
	};
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<canvas id="canvas" />
