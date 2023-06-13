<script setup>
import Logo from "../assets/logo.svg";
</script>

<template>
	<div class="main-header-wrapper">
		<div class="balance-container">
			<div class="balance-label">My balance</div>
			<div class="balance-value">$921.48</div>
		</div>
		<img :src="Logo" alt="logo" />
	</div>
</template>

<style scoped>
.main-header-wrapper {
	background-color: hsl(10, 79%, 65%);
	width: 100%;
	padding: 20px;
	border-radius: 10px;
	display: flex;
	justify-content: space-between;
}

.balance-container {
	display: flex;
	flex-direction: column;
	gap: 10px;
	color: #ffffff;
}

.balance-label {
	opacity: 0.8;
}

.balance-value {
	font-size: 20px;
	font-weight: 700;
}
</style>
