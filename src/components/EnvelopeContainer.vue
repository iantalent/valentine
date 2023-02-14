<template>
	<div :class="['container', opened ? 'active' : '']">
		<div class="back">
			<div class="paper">
				<div class="paper-container">
					<slot></slot>
					
					<img class="sapogov" alt="Ричард сапогов" src="../assets/sapogov.png">
				</div>
			</div>
			<div class="cover"></div>
			<div class="bottom"></div>
			<div class="heart" @click="onOpen"></div>
		</div>
	</div>
</template>

<script>
	export default {
		name: "EnvelopeContainer",
		data()
		{
			return {
				opened: false
			};
		},
		methods: {
			onOpen()
			{
				this.opened = true;
			}
		}
	};
</script>

<style scoped lang="scss">
	@import '../assets/variables';
	
	.paper {
		width: 25em;
		height: 15em;
		position: absolute;
		display: block;
		top: 2em;
		left: 2.5em;
		background: $paper;
		-webkit-transition: 1.5s ease-in-out;
		-moz-transition: 1.5s ease-in-out;
		transition: all 1.5s ease-in-out;
		z-index: 1;
		text-align: center;
		padding: 1em;
		box-sizing: border-box;
		border: 1px solid $paper-border-color;
		
		.paper-container {
			position: relative;
			display: block;
			height: 100%;
		}
		
		.sapogov {
			opacity: 0;
			position: absolute;
			bottom: $sapogov-bottom;
			left: auto;
			right: auto;
			width: $sapogov-size;
			height: auto;
		}
	}
	
	.back {
		display: block;
		position: relative;
		background: darken($envelop, 10%);
		top: 0;
		height: 0;
		width: 30em;
		height: 17em;
		content: "";
		-webkit-transition: 1.5s ease-in-out;
		-moz-transition: 1.5s ease-in-out;
		transition: all 1.5s ease-in-out;
		box-shadow: 0 0 1em rgba(darken($bgcolor, 30%), .15);
		z-index: 0;
		
		
	}
	
	.heart {
		position: absolute;
		top: 50%;
		left: 50%;
		width: $heart-size;
		height: $heart-size;
		background: $heart-color;
		z-index: 999;
		transform: translate(-50%, -20%) rotate(45deg);
		transition: transform 0.5s ease-in-out 1s;
		box-shadow: 0 1px 6px $heart-shadow-color;
		cursor: pointer;
		
		&:before, &:after {
			content: "";
			position: absolute;
			width: $heart-size;
			height: $heart-size;
			background-color: $heart-color;
			border-radius: 50%;
		}
		
		&:before {
			top: - $heart-pseudo-size;
		}
		
		&:after {
			right: $heart-pseudo-size;
		}
	}
	
	.container {
		margin: 0 auto 0 auto;
		padding: 10em 1em 1em 1em;
		width: 30em;
		height: 20em;
		position: relative;
		overflow: hidden;
		display: block;
		z-index: 0;
		transition: all 1.5s ease-in-out;
		
		.cover {
			position: absolute;
			top: 0em;
			left: 50%;
			height: 1em;
			display: block;
			-moz-transform: translate(-50%, 0%) scaleY(1);
			-webkit-transform: translate(-50%, 0%) scaleY(1);
			transform: translate(-50%, 0%) scaleY(1);
			-webkit-transform-origin: 0% 50%;
			-ms-transform-origin: 0% 50%;
			transform-origin: 0% 50%;
			margin: 0 auto;
			border: 15em solid transparent;
			border-top: 10em solid lighten($envelop, 12%);
			-webkit-transition: all 1.5s ease-in-out;
			-moz-transition: all 1.5s ease-in-out;
			transition: z-index 1.5s ease-in-out, transform 1.5s ease-in-out, border-top 1.5s ease-in-out;
			transition-delay: 1.5s;
			z-index: 30;
			
		}
		
		&.active {
			
			.back {
				top: 10em;
				z-index: 0;
				.paper {
					top: -15em;
					z-index: 45;
					height: 30em;
					transition: z-index 1.5s ease-in-out, top 1.5s ease-in-out, height 1.5s ease-in-out;
					transition-delay: 1.5s;
				}
				
				.sapogov{
					opacity: 1;
					transition: opacity 1.5s ease-in-out;
					transition-delay: 2.5s;
				}
			}
			
			
			.cover {
				
				border-top: 10em solid $envelop;
				-moz-transform: translate(-50%, -100%) scaleY(-1);
				-webkit-transform: translate(-50%, -100%) scaleY(-1);
				transform: translate(-50%, -100%) scaleY(-1);
				z-index: 0;
				transition-delay: 0s;
				
			}
		}
		
		.bottom {
			
			width: 0;
			margin: 0 auto;
			position: relative;
			top: 0em;
			display: block;
			border-left: 15em solid $envelop;
			border-right: 15em solid $envelop;
			border-bottom: 7em solid $envelop;
			border-top: 10em solid transparent;
			-webkit-transition: 1.5s ease-in-out;
			-moz-transition: 1.5s ease-in-out;
			transition: 1.5s ease-in-out;
			z-index: 100;
			
		}
		
	}
</style>