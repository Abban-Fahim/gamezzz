<script>
	import { onMount } from 'svelte';
	import { Canvas, Layer, t } from 'svelte-canvas';
	let score = 2;

	let snake = {
		path: [
			[10, 10],
			[200, 10],
			[200, 200]
		],
		length: 2,
		dx: 0,
		dy: 1
	};

	onMount(() => {
		window.addEventListener('keydown', (e) => {
			switch (e.key) {
				case 'ArrowUp':
					dy = -1;
					dx = 0;
					break;
				case 'ArrowDown':
					dy = 1;
					dx = 0;
					break;
				case 'ArrowLeft':
					dx = -1;
					dy = 0;
					break;
				case 'ArrowRight':
					dx = 1;
					dy = 0;
					break;
			}
		});
	});

	/**
	 * @type {import("svelte-canvas").Render}
	 */
	let render = ({ context, width, height }) => {
		context.beginPath();
		context.fillStyle = `hsl(${$t / 40}, 100%, 50%)`;
		context.beginPath();
		context.font = '36px sans-serif yellow';
		context.strokeText('Score: ' + score, 100, 100);
		for (var i = 0; i < snake.path.length - 1; i++) {
			context.rect(
				snake.path[i][0],
				snake.path[i][1],
				(snake.path[i + 1][0] / snake.path[i][0]) * 10,
				(snake.path[i + 1][1] / snake.path[i][1]) * 10
			);
			context.fill();
		}
		for (var i = 0; i < snake.path.length - 1; i++) {
			if (snake.path[i + 1][0] !== snake.path[i][0]) {
				snake.path[i][0] += 10;
			}
			if (snake.path[i + 1][1] !== snake.path[i][1]) {
				snake.path[i][1] += 10;
			}
		}
		console.log(snake.path);
		context.closePath();
		setTimeout(render, 5000);
	};
</script>

<h1>SNAKEEEEEEEEEE</h1>
<Canvas width="600" height="600">
	<Layer {render} />
</Canvas>
