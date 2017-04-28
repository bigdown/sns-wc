<template>
	<div id="example-4">
		<button @click="show = !show">
    Toggle
  </button>
		<transition v-on:before-enter="beforeEnter" v-on:enter="enter" v-on:leave="leave" v-bind:css="false">
			<p v-if="show">
				Demo
			</p>
		</transition>
	</div>
</template>

<script>
	/* eslint-disable */
	import '../assets/css/animate.min.css'
	import Velocity from 'velocity-animate/velocity.min.js'
	export default {
		name: 'welcome',
		el: '#example-4',
		data() {
			return {
				show: false
			}
		},
		beforeMount: function() {
			console.log('123');
			//	this.show = true;
		},
		methods: {
			beforeEnter: function(el) {
				el.style.opacity = 0
				el.style.transformOrigin = 'left'
			},
			enter: function(el, done) {
				Velocity(el, {
					opacity: 1,
					fontSize: '1.4em'
				}, {
					duration: 300
				})
				Velocity(el, {
					fontSize: '1em'
				}, {
					complete: done
				})
			},
			leave: function(el, done) {
				Velocity(el, {
					translateX: '15px',
					rotateZ: '50deg'
				}, {
					duration: 600
				})
				Velocity(el, {
					rotateZ: '100deg'
				}, {
					loop: 2
				})
				Velocity(el, {
					rotateZ: '45deg',
					translateY: '30px',
					translateX: '30px',
					opacity: 0
				}, {
					complete: done
				})
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>