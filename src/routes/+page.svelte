<script>
	// https://github.com/gstefanic/svelte-transcription-player
	import { onMount } from 'svelte';

	onMount(() => {
		new TranscriptionPlayer({
			target: document.body,
			props: {
				audio: 'demo.mp3',
				transcription: 'demo.json',
				playerHeight: 'small'
			}
		});
	});
</script>
