<template>
	<section class="main" v-cloak>
		<input class="toggle-all" type="checkbox" v-model="allDone">
		<ul class="todo-list">
			<todo-item v-for="todo in filteredTodos" :todo="todo" :index="$index"></todo-item>
		</ul>
	</section>
</template>
<script>
	import store from './store.js'
	import TodoItem from './TodoItem.vue'
	
	export default{
		props:['filteredTodos'],
		computed:{
			allDone:{
				get(){
					return store.filters.active(store.state.todos).length===0;
				},
				set(value){
					store.state.todos.forEach(todo=>{todo.completed=value})
				}
			}
		},
		components:{
			TodoItem
		},

	}
</script>
<style lang="sass">
	.main {
		position: relative;
		z-index: 2;
		border-top: 1px solid #e6e6e6;
	}

	label[for='toggle-all'] {
		display: none;
	}

	.toggle-all {
		position: absolute;
		top: -55px;
		left: -12px;
		width: 60px;
		height: 34px;
		text-align: center;
		border: none; /* Mobile Safari */
	}

	.toggle-all:before {
		content: '❯';
		font-size: 22px;
		color: #e6e6e6;
		padding: 10px 27px 10px 27px;
	}

	.toggle-all:checked:before {
		color: #737373;
	}

	.todo-list {
		margin: 0;
		padding: 0;
		list-style: none;
	}
</style>