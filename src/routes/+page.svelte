<script>
	import { onMount } from 'svelte';

	// https://github.com/hyperaudio/hyperaudio-lite
	// https://hyperaudio.github.io/hyperaudio-lite-editor/
	const newPlayer = () => {
		new TranscriptionPlayer({
			target: document.body,
			props: {
				audio: 'demo.mp3',
				transcription: 'demo.json',
				playerHeight: 'small'
			}
		});
	};

	onMount(() => {
		const script = document.createElement('script');
		script.src = '/transcription.js';
		script.async = true;
		script.onload = () => {
			newPlayer();
		};

		document.head.appendChild(script);

		return () => {
			document.head.removeChild(script);
		};
	});
</script>

<svelte:head>
	<!-- <script async src="https://svelte-transcription-player.vercel.app"></script> -->
	<!-- <script async src="transcription.js" on:load={newPlayer()}></script> -->
</svelte:head>
