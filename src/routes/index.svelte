<script lang="ts">
	import { browser } from '$app/env';
	import * as B from 'babylonjs';
	import type { Engine, Scene, Camera, HemisphericLight, Mesh } from 'babylonjs';

	let canvas: HTMLCanvasElement;
	let engine: Engine;
	let scene: Scene;
	let box: Mesh;

	const createScene = (): Scene => {
		const scene = new B.Scene(engine);

		const camera = new B.FreeCamera('camera', new B.Vector3(0, 0, -5), scene);
		camera.attachControl(canvas, true);
		const light = new B.HemisphericLight('light', new B.Vector3(0, 1, 0), scene);

		box = B.MeshBuilder.CreateBox(
			'box',
			{
				size: 10
			},
			scene
		);

		return scene;

		// const scene = new B.Scene(engine);

		// const camera = new B.ArcRotateCamera(
		// 	'camera',
		// 	-Math.PI / 2,
		// 	Math.PI / 2.5,
		// 	3,
		// 	new B.Vector3(0, 0, 0)
		// );
		// camera.attachControl(canvas, true);

		// const light = new B.HemisphericLight('light', new B.Vector3(0, 1, 0), scene);

		// box = B.MeshBuilder.CreateBox('box', {});

		// console.log('BOX', box, light, camera);

		// return scene;
	};

	if (browser) {
		canvas = document.getElementById('canvas') as HTMLCanvasElement;
		engine = new B.Engine(canvas, true);
		// scene = new B.Scene(engine);
		scene = createScene();
		engine.runRenderLoop(() => {
			console.log('rendering');
			scene.render();
		});
	}

	$: console.log('%ccanvas', 'color:magenta', canvas);
	$: console.log('%cengine', 'color:orange', engine);
	$: console.log('%cscene', 'color:lime', scene);
	$: console.log('%cbox', 'color:lime', box);
</script>

<canvas id="canvas" class="bg-black h-[80vh] w-[80vw]" />
