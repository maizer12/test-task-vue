<template>
	<div class="filter">
		<h4 class="filter__title mb-3">Category:</h4>
		<ul class="filter-items m-0 p-0 d-flex">
			<li
				:class="[
					'filter-items__item',
					'btn',
					filter === item ? 'btn-dark' : 'btn-light',
				]"
				@click="updateFilter(item)"
				:key="item"
				v-for="item in items"
			>
				{{ item }}
			</li>
		</ul>
	</div>
</template>

<script>
import { filterItems } from '@/_config'
import { mapState, mapMutations } from 'vuex'

export default {
	data() {
		return {
			items: filterItems,
		}
	},
	computed: {
		...mapState({
			filter: state => state.products.filter,
		}),
	},
	methods: {
		...mapMutations({
			setFilter: 'products/setFilter',
		}),
		updateFilter(filterName) {
			this.setFilter(filterName)
		},
	},
	mounted() {},
}
</script>

<style scoped>
.filter-items {
	list-style: none;
	column-gap: 25px;
}
</style>
