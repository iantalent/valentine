<template>
	<div>
		<EnvelopeContainer>
			<h1>Дорогая особа!</h1>
			
			<p>В этот день любви я хочу сказать <br>как много ты значишь для меня.<br> Хочу тебя пригласить на свидание.</p>
		</EnvelopeContainer>
	</div>
</template>

<script>
	import EnvelopeContainer from "@/components/EnvelopeContainer";
	
	export default {
		name: 'App',
		components: {EnvelopeContainer}
	};
</script>

<style lang="scss">
	@import "assets/variables";
	
	html, body {
		width: 100%;
		height: 100%;
	}
	
	#app {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100%;
	}
	
	body {
		background: $bgcolor;
		padding: 0;
		margin: 0;
		position: relative;
		font-family: 'Marck Script', sans-serif;
	}
	
	body h1 {
		font-size: $h1-size;
		line-height: $h1-size + 2px;
		margin: 5px 0 35px;
	}
	
	body p {
		font-size: $text-size;
		line-height: $text-size + 2px;
	}
</style>
