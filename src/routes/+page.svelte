<script>
	import { onMount, onDestroy } from 'svelte';

	let scriptLoaded = false;

	onMount(() => {
		const script = document.createElement('script');
		script.src = 'transcription.js';
		script.async = true;
		script.onload = () => {
			scriptLoaded = true;
		};
		script.onerror = () => {
			console.error('Failed to load the transcription script');
		};
		document.head.appendChild(script);

		// Cleanup function
		onDestroy(() => {
			script.remove();
		});
	});

	// Reactive statement to initialize the player only when the script is loaded
	$: if (scriptLoaded) {
		new TranscriptionPlayer({
			target: document.body,
			props: {
				audio: 'demo.mp3',
				transcription: 'demo.json',
				playerHeight: 'small'
			}
		});
	}
</script>
