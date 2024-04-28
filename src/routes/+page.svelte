<script>
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
</script>

<svelte:head>
	<!-- <script async src="https://svelte-transcription-player.vercel.app"></script> -->
	<script async src="transcription.js" on:load={newPlayer()}></script>
</svelte:head>
