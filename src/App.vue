<script setup>
import MainHeader from "./components/MainHeader.vue";
import MainContent from "./components/MainContent.vue";
</script>

<template>
	<div class="main-wrapper">
		<MainHeader />
		<MainContent />
	</div>
</template>

<style scoped>
.main-wrapper {
	width: 100%;
	padding: 10px;
	display: flex;
	flex-direction: column;
	gap: 20px;
	max-width: 550px;
	margin: 0 auto;
	margin-top: 50px;
}
</style>
