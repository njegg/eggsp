<script>
	import Grid from "./components/Grid.svelte";
	import Taskbar from "./ui/Taskbar.svelte";

	let n = 16
	let m = 9

	let icons = Array(n * m, undefined)
	icons[0] = { src: '../img/icons8-txt-file-64.png' }
	icons[1] = { src: '../img/icons8-txt-file-64.png' }

</script>


<main>
	<Grid {n} {m} {icons}></Grid>
</main>

<Taskbar/>


<style>
	main {
		background-image: url('/img/wallpeper.jpeg');
		height: 100%;
	}
</style>