<template>
	<div id="app" class="container mt-5">
		<div class="row">
			<div class="col form-inline">
				<b-form-input
					v-model="newItem"
					required
					placeholder="回车键添加项目"
					@keyup.enter="add"
				></b-form-input>
				<b-button @click="add" variant="primary ml-3">添加</b-button>
			</div>
		</div>
		<div class="row mt-5">
			<div class="col-3">
				<div class="p-2 alert alert-secondary">
					<h3>项目集</h3>
					<draggable class="list-group height" v-model="items" group="group">
						<div class="list-group-item" v-for="(element, index) in items" :key="index">
							{{ element.name }}
						</div>
					</draggable>
				</div>
			</div>
			<div class="col-3">
				<div class="p-2 alert alert-primary">
					<h3>项目集 A</h3>
					<draggable class="list-group height" v-model="itemsA" group="group">
						<div
							class="list-group-item"
							v-for="(element, index) in itemsA"
							:key="index"
						>
							{{ element.name }}
						</div>
					</draggable>
				</div>
			</div>
			<div class="col-3">
				<div class="p-2 alert alert-warning">
					<h3>项目集 B</h3>
					<draggable class="list-group height" v-model="itemsB" group="group">
						<div
							class="list-group-item"
							v-for="(element, index) in itemsB"
							:key="index"
						>
							{{ element.name }}
						</div>
					</draggable>
				</div>
			</div>
			<div class="col-3">
				<div class="p-2 alert alert-success">
					<h3>项目集 C</h3>
					<draggable class="list-group height" v-model="itemsC" group="group">
						<div
							class="list-group-item"
							v-for="(element, index) in itemsC"
							:key="index"
						>
							{{ element.name }}
						</div>
					</draggable>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
// 导入 vuedraggable
import draggable from 'vuedraggable'

export default {
	name: 'App',
	data() {
		return {
			newItem: '',
			items: [{ name: '项目 1' }, { name: '项目 2' }, { name: '项目 3' }],
			itemsA: [],
			itemsB: [],
			itemsC: [],
		}
	},
	methods: {
		add() {
			if (this.newItem) {
				this.items.push({ name: this.newItem })
				this.newItem = ''
			}
		},
	},
	components: { draggable },
}
</script>

<style>
.height {
	min-height: 300px;
}
</style>
