<script>
	import {Router, Route, Link} from 'svelte-navigator';
import Home from './Home.svelte';
	import Weather from "./Weather.svelte";
</script>


<Router>
	<Route path="/">
			<Home/>
	</Route>
	<Route path="/weather">
		<Weather/>
	</Route>

</Router>

