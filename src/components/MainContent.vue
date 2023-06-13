<script setup>
import chartJSON from "../../data.json";
import { ref } from "vue";

const chartData = chartJSON;
const hoverIndex = ref(null);
const activeIndex = ref(null);
</script>

<template>
	<div class="main-content-wrapper">
		<p class="content-header">Spending - Last 7 days</p>
		<div class="chart-container">
			<div
				v-for="(data, index) in chartData"
				:key="data.day"
				class="chart-content"
				:class="['chart-content', { active: activeIndex === index }]"
				@click="activeIndex = index"
			>
				<div style="position: relative">
					<div
						class="chart-bar-tooltip"
						v-show="hoverIndex === index || activeIndex === index"
					>
						${{ data.amount }}
					</div>
				</div>
				<div
					class="chart-bar"
					:style="{
						height: data.amount + '%',
						backgroundColor:
							activeIndex === index ? 'hsl(186, 34%, 60%)' : '',
					}"
					@mouseenter="hoverIndex = index"
					@mouseleave="hoverIndex = null"
				></div>
				<div class="chart-label">{{ data.day }}</div>
			</div>
		</div>

		<div class="content-footer">
			<div class="current-month-container">
				<p class="current-month-label">Total this month</p>
				<p class="current-month-value">$478.33</p>
			</div>

			<div class="last-month-container">
				<p class="last-month-value">+2.4%</p>
				<p class="last-month-label">from last month</p>
			</div>
		</div>
	</div>
</template>

<style scoped>
.main-content-wrapper {
	background-color: #ffffff;
	min-height: 400px;
	padding: 20px;
}

.content-header {
	color: hsl(25, 47%, 15%);
	font-size: 25px;
	font-weight: 700;
	border-radius: 10px;
}

.chart-container {
	display: flex;
	height: 100%;
	width: 100%;
	justify-content: space-between;
	/* gap: 15px; */
	margin-top: 50px;
	margin-top: 50px;
}

.chart-content {
	width: calc(100% / 7);
	height: 400px;
	display: flex;
	flex-direction: column;
	justify-content: flex-end;
}

.chart-bar {
	height: 90%;
	/* margin: 0 auto; */
	width: 80%;
	margin: 0 auto;
	background-color: hsl(10, 79%, 65%);
	border-radius: 5px;
	position: relative;
	display: flex;
}

.chart-bar:hover {
	opacity: 0.8;
	cursor: pointer;
}

.chart-bar-tooltip {
	position: absolute;
	top: -40px;
	border-radius: 5px;
	background-color: hsl(25, 47%, 15%);
	padding: 5px;
	width: 100%;
	text-align: center;
	color: white;
	font-weight: 700;
}

.chart-label {
	height: 10%;
	display: flex;
	justify-content: center;
	align-items: center;
	color: hsl(28, 10%, 53%);
}

.content-footer {
	border-top: 2px solid hsl(27, 66%, 92%);
	margin-top: 20px;
	padding-top: 30px;
	display: flex;
	justify-content: space-between;
	align-items: flex-end;
	color: hsl(25, 47%, 15%);
}

.current-month-container {
	display: flex;
	flex-direction: column;
	gap: 10px;
}

.current-month-label {
	opacity: 0.6;
}

.current-month-value {
	font-weight: 700;
	font-size: 30px;
}

.last-month-container {
	text-align: right;
}

.last-month-value {
	font-weight: 700;
}

.last-month-label {
	opacity: 0.6;
}

@media screen and (max-width: 480px) {
	.chart-bar-tooltip {
		font-size: 13px;
		top: -35px;
	}
}
</style>
