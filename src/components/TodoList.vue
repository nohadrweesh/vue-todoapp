<template>
  <div >
  	<input type="text" class="todo-input" placeholder="What needs to be done?" v-model="newTodo" @keyup.enter="addNewTodo">
  	<div v-for="(todo,index) in todos" :key="todo.id"  class="todo-item">
  		<div>
  		{{todo.title}}
  		</div>
  		<div class="remove-item" @click="removeTodo(index)">
  			&times;
  		</div>
  	</div>
   
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
     newTodo:'',
     idForTodo:3,
     todos:[
     			{
     				'id':1,
     				'title':'todo 1',
     				'completed':false
     			},
     			{
     				'id':2,
     				'title':'todo 2',
     				'completed':false
     			}
     ]
    }
  },methods:{
  	addNewTodo(){
  		if(this.newTodo.trim().length==0){
  			return
  		}
  		this.todos.push({
  			'id':this.idForTodo,
  			'title':this.newTodo,
  			'completed':false
  		});
  		this.idForTodo=	this.idForTodo+1;
  		this.newTodo='';
  	},
  	removeTodo(index){
  		this.todos.splice(index,1)
  	}

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.todo-input{
	width:100%;
	padding:10px 18px;
	margin-bottom:10px;
	&:focus {
		outline:0;
	}
}
.todo-item{
	margin-bottom:12px;
	display:flex;
	align-items:center;
	justify-content:space-between;
}
.remove-item{
	margin-right:-35px;
	cursor:pointer;
	&:hover{
		color:black;
	}
}

</style>
