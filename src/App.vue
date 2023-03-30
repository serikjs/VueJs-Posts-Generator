<template>
	<div class="container column">
		<Form @updateData="formUpdate" />
		<Portfolio :blocks="portfolioData" />
	</div>
	<div class="container">
		<Loader v-if="isConnect" />
		<Coments v-else :comments="comments" @loadComments="loadComments" />
	</div>
</template>

<script>
import Form from './components/Form.vue'
import Portfolio from './components/Portfolio.vue'
import Coments from './components/Coments.vue'
import Loader from './components/Loader.vue'
export default {
	components: { Form, Portfolio, Coments, Loader },
	data() {
		return {
			portfolioData: [],
			comments: [],
			isConnect: false,
		}
	},
	methods: {
		formUpdate(block) {
			this.portfolioData.push({
				type: block.type,
				value: block.value,
			})
		},
		loadComments() {
			this.isConnect = true
			setTimeout(() => {
				this.comments = [
					{
						autor: 'test@microsoft.com',
						text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eligendi,reiciendis.',
					},
				]
				this.isConnect = false
			}, 2000)
		},
	},
}
</script>

<style>
.avatar {
	display: flex;
	justify-content: center;
}

.avatar img {
	width: 150px;
	height: auto;
	border-radius: 50%;
}
</style>
