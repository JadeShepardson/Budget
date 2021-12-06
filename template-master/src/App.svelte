<script>
	class Budget {
		//completed boolean
		//text string
		constructor(name, value, weight) {
			this.name = name;
			this.val = value;
			this.weight = weight;
		}
	}
	let budgets = [
		new Budget("Rent", 0, 0),
		new Budget("Food", 0, 0),
		new Budget("Utilities", 0, 0)
	]
	const add_budget = () => {
		budgets = budgets.concat([new Budget("Item", 0, 0)])
	}
	const delete_budget = (item_to_delete) => {
		if(confirm("Delete " + item_to_delete + "?")) {
			budgets = budgets.filter((budget) => budget !== item_to_delete)
		}
	}
	const calculate_budget = () => {

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
			"item value weight del_button"
			/2fr 1fr 1fr auto
		;
		column-gap: 10px;
	}	 
	[id=item] {
		grid-area: item;
	}
	[id=value] {
		grid-area: value;
	}
	[id=weight] {
		grid-area: weight;
	}
	[id=del_button] {
		grid-area: del_button;
	}
	button {
		border: 1px solid black;
		border-radius: 5px;
		font-weight: bold;
	}
</style>
<body>
	<header>
		<h1>Easy Budget</h1>
	</header>
	
	<div id="info">
		<h3>What is Easy Budget?</h3>
		<p>Hello. This is Easy Budget, a web app designed to help you budget. Using combinatorial optimization via the Knapsack Problem, Easy Budget can help determine how to best use your money.</p>
		<h3>How to Use Easy Budget?</h3>
		<p>To start, determine the weight of your "knapsack" or how much money you have for this period in the "Total Budget" box.</p>
		<p>Next add in your expenses using the item, value, and weight boxes. The item is the expenese, the value is how important it is from 0 to 10 (0 being most important and 10 being least), and the weight is how much each item costs.</p>
		<p>So if your rent is $700, you'd want to put "rent" in the item box, "0" in the value box and "700" in the weight box.</p>
		<p>The submit button is for when you are ready so see your generated budget. The more button gives you more items to add to your potential budget.</p>
	</div>
	
	<div id = "input">
		<div id="totalBudget"><span>Total Budget:</span><input type = "number" min="0"/></div>
		<br>
		{#each budgets as budget}

		<budget-item>
			<div id="item"><span>Item:</span><input type = "text" bind:value={budget.name}/></div>
			<div id="value"><span>Value: </span><input type = "number" min="0" max="10" bind:value={budget.val}/></div>
			<div id="weight"><span>Weight: </span><input type = "number" min="0" bind:value={budget.weight}/></div>
			<div id="del_button"><button on:click={() => delete_budget(budget)}>X</button></div>
		</budget-item>
		{/each}
		<button on:click={add_budget}>Add Item</button>
		<button on:click={calculate_budget}>Submit</button>
	</div>
	
	<div id="output">
		<p>output</p>
		<p>How do i want to do this in order to make this as fast as possible??? I can make it so that the items are immediately put into an array. This array is then sorted via sorting algorithm (heap sort or meergesort or quicksort) by weight and value (value being how necessary and weight being how much). Algorithm then goes through and puts items in the "knapsack" accordingly. Ta-da! Not best solution but a solution all the same. </p>
	</div>
	
	<footer>
		<p>Copyright and privacy blah blah blah</p>
	</footer>
</body>