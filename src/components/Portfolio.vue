<template>
	<div class="card card-w70">
		<template
			v-if="isData"
		>
			<component
				v-for="block in blocks"
				:key="block.id"
				:is="block.type"
				v-bind="{ value: block.value }"
			></component>
		</template>

		<h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
	</div>
</template>
<script>
import Title from './Title.vue'
import Avatar from './Avatar.vue'
import Subtitle from './Subtitle.vue'
import Text from './Text.vue'
export default {
	components: { Title, Avatar, Subtitle, Text },
	props: {
		blocks: {
			type: Array,
			require: true,
		},
	},
	data() {
		return {}
	},
	methods: {},
	computed: {
		isData() {
			return this.blocks.length > 0
		},
	},
}
</script>
<style scoped></style>
