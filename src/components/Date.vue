<template>
	<div class="date-component">{{ formattedDate }}</div>
</template>

<script>
	export default {
		props: {
			currentDate: {
				type: String, 
				default: '2020-03-12'
			}
		},

		computed: {
			formattedDate() {
				const dateObject = new Date(this.currentDate);
				const year = dateObject.getFullYear();
				const month = dateObject.getMonth();
				const date = dateObject.getDate();

				return `${date}.${month + 1}.${year}`
			}
		}
	}
</script>