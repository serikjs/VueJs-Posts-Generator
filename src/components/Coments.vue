<template>
	<p v-if="!isComments">
		<button class="btn primary" @click="$emit('loadComments')">
			Загрузить комментарии
		</button>
	</p>

	<div class="card" v-else>
		<h2>Комментарии</h2>
		<ul class="list">
			<li class="list-item" v-for="(comment, index) in comments" :key="index">
				<div>
					<p>
						<strong>{{ comment.autor }}</strong>
					</p>
					<small>{{ comment.text }}</small>
				</div>
			</li>
		</ul>
	</div>
</template>
<script>
export default {
	emits: ['loadComments'],
	props: ['comments'],
	components: {},
	data() {
		return {
			isConnect: false,
		}
	},
	methods: {},
	computed: {
		isComments() {
			return this.comments.length > 0
		},
	},
}
</script>
<style scoped></style>
