<script lang="ts">
	import { Avatar } from '@skeletonlabs/skeleton';

	let testimonials = [
		{
			name: 'John Smith',
			avatar:
				'https://plus.unsplash.com/premium_photo-1680020185326-45491267f8da?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=687&q=80',
			text: "I couldn't be happier with the upholstery work done by this company. My old furniture looks brand new again!"
		},
		{
			name: 'Sarah Johnson',
			avatar:
				'https://images.unsplash.com/photo-1580489944761-15a19d654956?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=761&q=80',
			text: 'The attention to detail and craftsmanship is exceptional. I highly recommend their services to anyone in need of upholstery work.'
		},
		{
			name: 'Michael Anderson',
			avatar:
				'https://images.unsplash.com/photo-1499996860823-5214fcc65f8f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=766&q=80',
			text: 'From start to finish, the team at this upholstery company was professional and friendly. My furniture was completed on time and exceeded my expectations.'
		},
		{
			name: 'Lisa Martinez',
			avatar:
				'https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=686&q=80',
			text: 'I was hesitant to reupholster my antique chair, but it was the best decision I made. The result is stunning, and I get compliments from everyone who sees it.'
		}
	];
	let state = 1;
	$: active = testimonials[state];
	let leftSide = testimonials[0];
	let rightSide = testimonials[2];

	function goRight() {
		if (state == testimonials.length - 1) {
			state = 0;
			rightSide = testimonials[state + 1];
			leftSide = testimonials[testimonials.length - 1];
		} else {
			state++;
			if (state == testimonials.length - 1) {
				rightSide = testimonials[0];
			} else {
				rightSide = testimonials[state + 1];
			}
			if (state == 0) {
				leftSide = testimonials[testimonials.length - 1];
			} else {
				leftSide = testimonials[state - 1];
			}
		}
	}
	function goLeft() {
		if (state == 0) {
			state = testimonials.length - 1;
			rightSide = testimonials[0];
			leftSide = testimonials[state - 1];
		} else {
			state--;
			if (state == testimonials.length - 1) {
				rightSide = testimonials[0];
			} else {
				rightSide = testimonials[state + 1];
			}
			if (state == 0) {
				leftSide = testimonials[testimonials.length - 1];
			} else {
				leftSide = testimonials[state - 1];
			}
		}
	}
</script>

<div class="card flex py-10 mt-4 relative">
	<div class="scroll-smooth flex overflow-x-auto justify-center gap-6">
		<div class="snap-center w-[25%] rounded-container-token blur-sm slide-in-right scaler">
			<Avatar src={leftSide.avatar} width="w-32" rounded="rounded" />
			<h3>{leftSide.name}</h3>
			<p>{leftSide.text}</p>
		</div>
		{#key state}
			<div class="snap-center w-[25%] rounded-container-token slide-in-right">
				<Avatar src={active.avatar} width="w-32" rounded="rounded" />
				<h3 class="text-lg pb-2">{active.name}</h3>
				<p>{active.text}</p>
			</div>
		{/key}
		<div class="snap-center w-[25%] rounded-container-token blur-sm slide-in-right scaler">
			<Avatar src={rightSide.avatar} width="w-32" rounded="rounded" />
			<h3>{rightSide.name}</h3>
			<p>{rightSide.text}</p>
		</div>
	</div>
	<button class="absolute left-5 top-[45%] hover:bg-slate-700" on:click={goLeft}>
		<xml version="1.0" encoding="utf-8">
			<svg
				width="50px"
				height="50px"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M11 9L8 12M8 12L11 15M8 12H16M7.2 20H16.8C17.9201 20 18.4802 20 18.908 19.782C19.2843 19.5903 19.5903 19.2843 19.782 18.908C20 18.4802 20 17.9201 20 16.8V7.2C20 6.0799 20 5.51984 19.782 5.09202C19.5903 4.71569 19.2843 4.40973 18.908 4.21799C18.4802 4 17.9201 4 16.8 4H7.2C6.0799 4 5.51984 4 5.09202 4.21799C4.71569 4.40973 4.40973 4.71569 4.21799 5.09202C4 5.51984 4 6.07989 4 7.2V16.8C4 17.9201 4 18.4802 4.21799 18.908C4.40973 19.2843 4.71569 19.5903 5.09202 19.782C5.51984 20 6.07989 20 7.2 20Z"
					stroke="#000000"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</xml></button
	>
	<button class="absolute right-5 top-[45%] hover:bg-slate-700" on:click={goRight}>
		<xml version="1.0" encoding="utf-8">
			<svg
				width="50px"
				height="50px"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M13 15L16 12M16 12L13 9M16 12H8M7.2 20H16.8C17.9201 20 18.4802 20 18.908 19.782C19.2843 19.5903 19.5903 19.2843 19.782 18.908C20 18.4802 20 17.9201 20 16.8V7.2C20 6.0799 20 5.51984 19.782 5.09202C19.5903 4.71569 19.2843 4.40973 18.908 4.21799C18.4802 4 17.9201 4 16.8 4H7.2C6.0799 4 5.51984 4 5.09202 4.21799C4.71569 4.40973 4.40973 4.71569 4.21799 5.09202C4 5.51984 4 6.07989 4 7.2V16.8C4 17.9201 4 18.4802 4.21799 18.908C4.40973 19.2843 4.71569 19.5903 5.09202 19.782C5.51984 20 6.07989 20 7.2 20Z"
					stroke="#000000"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</xml></button
	>
</div>

<style>
  .scaler{
    scale: 0.7 !important;
  }
	.slide-in-right {
		-webkit-animation: slide-in-right 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
		animation: slide-in-right 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
	}
	@-webkit-keyframes slide-in-right {
		0% {
			-webkit-transform: translateX(30px);
			transform: translateX(30px);
			opacity: 0;
		}
		100% {
			-webkit-transform: translateX(0);
			transform: translateX(0);
			opacity: 1;
		}
	}

	@keyframes slide-in-right {
		0% {
			-webkit-transform: translateX(30px);
			transform: translateX(30px);
			opacity: 0;
		}
		100% {
			-webkit-transform: translateX(0);
			transform: translateX(0);
			opacity: 1;
		}
	}
</style>
