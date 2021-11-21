<script>
	class Budget {
		//completed boolean
		//text string
		constructor(name) {
			this.text = name;
		}
	}
	let budgets = [
		new Budget("Do Dishes"),
		new Budget("Dig Potatoes"),
		new Budget("Work at Job Factory")
	]
	const add_budget = () => {
		budgets = budgets.concat([new Budget("New Task")])
	}
	const delete_budget = (item_to_delete) => {
		if(confirm("Delete " + item_to_delete + "?")) {
			budgets = budgets.filter((budget) => budget !== item_to_delete)
		}
	}
</script>

<style>
	body {
    	background-color: lightsteelblue;
    	height: 100%;
		display: grid;
		grid-template:
	    	"header header" 65px
        	"info info"
	    	"input output"
	    	"footer footer" 50px
        	/1fr 1fr
	}
	header {
		grid-area: header;
	}
	[id=info] {
		grid-area: info;
	}
	[id=input] {
		grid-area: input;
		padding-right: 10px;
	}
	[id=output] {
		grid-area: output;
	}
	footer {
		grid-area: footer; 
	}
	budget-item {
		border: 1px solid black;
		padding: 10px;
		border-radius: 5px;
		box-sizing: border-box;
		width: 500px;
		display: grid;
		grid-template:
			"textfield button"
			/1fr auto
		;
		column-gap: 10px;
	}	 
	button {
		border: 1px solid black;
		border-radius: 5px;
		font-weight: bold;
	}
</style>
<body>
	<header>
		<h1>Elephant</h1>
	</header>
	
	<div id="info">
		<h3>What is Elephant?</h3>
		<p>Hello. This is Elephant, a web app designed to help you budget. Using combinatorial optimization via the Knapsack Problem, Elephant can help determine how to best use your money.</p>
		<h3>How to Use Elephant?</h3>
		<p>To start, determine the weight of your "knapsack" or how much money you have for this period in the "Total Budget" box.</p>
		<p>Next add in your expenses using the item, value, and weight boxes. The item is the expenese, the value is how important it is from 0 to 10 (1 being most important and 10 being least), and the weight is how much each item costs.</p>
		<p>The submit button is for when you are ready so see your generated budget. The more button gives you more items to add to your potential budget.</p>
	</div>
	
	<div id = "input">
		{#each budgets as budget}

		<budget-item class="{budget.completed ? 'completed' : ''}">
			<input type = "text" bind:value={budget.text}/>
			<button ont:click={() => delete_budget(budget)}>X</button>
		</budget-item>
		{/each}
		<button on-click={add_budget()}>Add Item</button>
	</div>
	
	<div id="output">
		<p>output</p>
		<p>How do i want to do this in order to make this as fast as possible??? I can make it so that the items are immediately put into an array. This array is then sorted via sorting algorithm (heap sort or meergesort or quicksort) by weight and value (value being how necessary and weight being how much). Algorithm then goes through and puts items in the "knapsack" accordingly. Ta-da! Not best solution but a solution all the same. </p>
	</div>
	
	<footer>
		<p>Copyright and privacy blah blah blah</p>
	</footer>
</body>