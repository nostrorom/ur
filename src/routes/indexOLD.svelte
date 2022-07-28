<script lang="ts">
	import { browser } from '$app/env';
	import * as BABYLON from 'babylonjs';

	let canvas: HTMLCanvasElement;
	let engine: BABYLON.Engine;

	const createScene = () => {
		const scene = new BABYLON.Scene(engine);

		const camera = new BABYLON.ArcRotateCamera(
			'camera',
			-Math.PI / 2,
			Math.PI / 2.5,
			3,
			new BABYLON.Vector3(0, 0, 0)
		);
		camera.attachControl(canvas, true);

		const light = new BABYLON.HemisphericLight('light', new BABYLON.Vector3(0, 1, 0));

		const box = BABYLON.MeshBuilder.CreateBox('box', {});

		return scene;
	};

	if (browser) {
		canvas = document.getElementById('canvas') as HTMLCanvasElement;
		engine = new BABYLON.Engine(canvas, true, { preserveDrawingBuffer: true, stencil: true });

		const scene = new BABYLON.Scene(engine);

		const camera = new BABYLON.ArcRotateCamera(
			'camera',
			-Math.PI / 2,
			Math.PI / 2.5,
			3,
			new BABYLON.Vector3(0, 0, 0),
			scene
		);
		camera.attachControl(canvas, true);

		const light = new BABYLON.HemisphericLight('light', new BABYLON.Vector3(0, 1, 0), scene);

		const box = BABYLON.MeshBuilder.CreateBox('box', {}, scene);
	}
</script>

<h1 class="text-lg text-orange-700">Welcome to UR</h1>

<canvas id="canvas" class="bg-blue-900" />
