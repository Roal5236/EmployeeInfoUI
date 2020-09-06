<script>
	import Tile from './Components/Tile/Tile.svelte';
	import EmployeeDataRow from './Components/Tile/EmployeeDataRow/EmployeeDataRow.svelte';
	import Form from './Components/Form.svelte';

	let employee= [
	{id:'1', fname:'Shantanu', lname:'Priyadarshi', phone:'8789893335', email:'shantanu09121998@gmail.com'},
	{id:'2', fname:'Rohaan', lname:'Almeida', phone:'8789893335', email:'shantanu09121998@gmail.com'},
	{id:'3', fname:'Manan', lname:'Tyagi', phone:'8789893335', email:'shantanu09121998@gmail.com'},
	{id:'4', fname:'Somil', lname:'Dua', phone:'8789893335', email:'shantanu09121998@gmail.com'}
	]
	let popupvisible=false;
	function togglepopup(){
		if(popupvisible)
		{
			document.getElementById('pop-up-id').style.display='none';
		}
		else{
			document.getElementById('pop-up-id').style.display='block';

		}
		popupvisible = !popupvisible;
	}
	function handleMessage(event) {
		var msg=event.detail.text;
		if (msg=="popup") {
			togglepopup();
		}
		else if(msg=="save"){
			CreateNewEntry(event.detail.fname,event.detail.lname,event.detail.phone,event.detail.company,event.detail.email);
			togglepopup();
		}
		else if(msg=="saveNew")
		{
			CreateNewEntry(event.detail.fname,event.detail.lname,event.detail.phone,event.detail.company,event.detail.email);
		}
        
    }
	function CreateNewEntry(fname2,lname2,phone2,company2,email2)
	{
		var id2= employee.length + 1;
		var temp= {id:id2, fname:fname2, lname:lname2, phone:phone2, email:email2};
		employee=[...employee,temp];
		console.log(employee);
	}
	
</script>
<body>
<div class="row" style="width:100%; height:45px; background-color:white; box-shadow:0px 0px 20px 1px">
<img src="slogo.jpg" style="width:10%; margin-left:2%"/>
<div class ="navlinks row" >
	<p>Home</p>
	<p>Products</p>
	<p>Services</p>
	<p>Support</p>
	<p>About us</p>
	<p>Contact us</p>

</div>
</div>	
<div style="width: 100%;background-color: #008028;height: 500px;position: absolute;z-index: -1;">
</div>

<div id='pop-up-id' style="position:relative;width:100%; display: none">
	<div style = "width:100%;background-color:rgba(0,0,0,0.5); position:absolute; padding-top:10%;height:100vh" >
	<Form on:message={handleMessage}/>

</div>
</div>
<div class="info-container col">
	<div>

	</div>
	<div class="tile-container row">
		<Tile Tile_Title={"All users"} Tile_Data={"1000"}/>

		<Tile Tile_Title={"Active Users"} Tile_Data={"500"}/>
		<Tile Tile_Title={"Inactive Users"} Tile_Data={"200"}/>
		<Tile Tile_Title={"Logins"} Tile_Data={"900"}/>
		<Tile Tile_Title={"Tickets"} Tile_Data={"215"}/>
	</div>
</div>

<div class="table-search-container">
	<div class="row searching-container">
		
		<div class="row long-rowz">
			<div class="search-container row" >
				<!-- svelte-ignore a11y-missing-attribute -->
				<img src="search_icon.png"/>
				<input class="search" placeholder="Search Here"/>
			</div>
		</div>

		<!-- <div class="long-row-button">
			Sort
		</div> -->

		<div class="long-row-button" on:click={() => togglepopup()}>
			<p class="new">New</p>
		</div>

		<div class="long-row-button">
			<p class="option">Option</p>
		</div>
	</div>

	<div class="col table-row-container">
	{#each employee as row}
	<EmployeeDataRow id={row.id} fname={row.fname} lname={row.lname} phone={row.phone} email={row.email}/>
	{/each}	
	</div>
	
</div>

</body>