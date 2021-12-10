<script>
	class Budget {
		constructor(name, value, weight) {
			this.name = name;
			this.val = value;
			this.weight = weight;
		} //budget constructor
	}//budget class
	let budgets = [
		new Budget("Rent", 0, 0),
		new Budget("Food", 0, 0),
		new Budget("Utilities", 0, 0)
	] //budgets list
	const add_budget = () => { //adds new budget item to budgets list
		budgets = budgets.concat([new Budget("Item", 0, 0)])
	} //add_budget
	const delete_budget = (item_to_delete) => { //deletes a selected budget from budgets list
		budgets = budgets.filter((budget) => budget !== item_to_delete)
	} //delete_budget
	const calculate_budget = () => { //calculates what can fit in one's budget
		var total_budget = document.getElementById('total').value;
		//document.getElementById("output").innerHTML = total_budget; //test code
		sort_budget

	} //calculate_budget
	const sort_budget = () => {
		//using quicksort algorithm for the running time and the storage costs
	} //sort_budget
	const partition = () => {
		//partition for the quicksort (sort_budget) algorithm
	} //partition
</script>

<style>
	body {
    	background-color: #00A86B; /*jade green :)*/
		color: white;
    	height: 100%;
		display: grid;
		grid-template:
	    	"header header" auto
        	"info info" auto
	    	"input output" 1fr
	    	"footer footer" auto
        	/1fr 1fr
	}
	p {
		padding-left: 10px;
		padding-right: 10px;
	}
	h1 {
		padding-left: 10px;
		padding-right: 10px;
	}
	h3 {
		padding-left: 10px;
		padding-right: 10px;
	}
	header {
		grid-area: header;
	}
	[id=info] {
		grid-area: info;
	}
	[id=input] {
		grid-area: input;
		padding: 10px;
		border: 5px solid black;
		border-radius: 5px;
	}
	[id=output] {
		grid-area: output;
		text-align: center;
		border: 5px solid black;
		padding: 10px;
		border-radius: 5px;
	}
	footer {
		grid-area: footer; 
	}
	[id=totalBudget] {
		text-align: center;
	}
	budget-item {
		margin: auto;
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
	[id=buttons] {
		display: flex;
		justify-content: center;
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
		<div id="totalBudget"><span>Total Budget:</span><input type = "number" min="0" id="total"/></div>
		<br>
		{#each budgets as budget}
			<budget-item>
				<div id="item"><span>Item:</span><input type = "text" bind:value={budget.name}/></div>
				<div id="value"><span>Value: </span><input type = "number" min="0" max="10" bind:value={budget.val}/></div>
				<div id="weight"><span>Weight: </span><input type = "number" min="0" bind:value={budget.weight}/></div>
				<div id="del_button"><button on:click={() => delete_budget(budget)}>X</button></div>
			</budget-item>
		{/each}
		<br>
		<div id="buttons">
			<button on:click={add_budget}>Add Item</button>
			<button on:click={calculate_budget}>Submit</button>
		</div>
	</div>
	
	<div id="output">
		<!--<p>output</p>
		<p>How do i want to do this in order to make this as fast as possible??? I can make it so that the items are immediately put into an array. This array is then sorted via sorting algorithm (heap sort or meergesort or quicksort) by weight and value (value being how necessary and weight being how much). Algorithm then goes through and puts items in the "knapsack" accordingly. Ta-da! Not best solution but a solution all the same. </p>-->

	</div>

	<footer>
		<p>Copyright © 2021 Jade Shepardson</p>
		<p>Privacy - Easy Budget retains none of your budgeting info so your information is safe and sound.</p>
	</footer>
</body>