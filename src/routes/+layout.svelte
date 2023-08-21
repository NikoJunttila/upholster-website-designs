<script lang='ts'>
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-vintage.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	// Most of your app wide CSS should be put in this file
	import '../app.postcss';
</script>
<style>
	    
</style>
<div class="max-w-[100vw] md:text-2xl lg:text-3xl overflow-hidden">
	<main>
		<slot />
	</main>
</div>
