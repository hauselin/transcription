<script>
	import { onMount } from 'svelte';

	onMount(() => {
		// Create a new script element
		const script = document.createElement('script');
		script.src = 'transcription.js';
		script.async = true;

		// Append the script to the head to start loading
		document.head.appendChild(script);

		// Function to initialize the transcription player
		function initializePlayer() {
			new TranscriptionPlayer({
				target: document.body,
				props: {
					audio: 'demo.mp3',
					transcription: 'demo.json',
					playerHeight: 'small'
				}
			});
		}

		// Set up the onload handler
		script.onload = () => {
			console.log('transcription.js loaded');
			initializePlayer();
		};

		// Optional: handle loading errors
		script.onerror = () => {
			console.error('Failed to load transcription.js');
		};
	});
</script>

<!-- Your Svelte component's HTML here -->
