<script>
	import { Router, Route, Link } from "svelte-routing";
	import Home from "./pages/Home.svelte";
	import About from "./pages/About.svelte";
	import Map from "./pages/Map.svelte";
	import List from "./pages/List.svelte";
	import Restaurant from "./pages/Restaurant.svelte";

	export let url = ""; 

</script>

<Router url="{url}">
	<div class="links">
		<nav class="dropdown">
			<button class="dropbtn">
				<svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/> </svg>
			</button>
			<ul class="dropdown-content">
				<li><Link to="/">Home</Link></li>
				<li><Link to="about">About</Link></li>
				<li><Link to="map">Map</Link></li>
			</ul>
		</nav>
	</div>
	<div>
		<Route path="/"><Home /></Route>
		<Route path="about" component="{About}"/>
		<Route path="map" component="{Map}"/>
		<Route path="list/*" component="{List}"/>
		<Route path="restaurant/:id" component="{Restaurant}"/>
		<Route path="restaurant/:id" let:params>
			<Restaurant id="{params.id}"/>
		</Route>
	</div>
</Router>