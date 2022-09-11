<script>
import { Link } from "svelte-navigator";


	const apiUrl = "https://api.openweathermap.org/data/2.5/";
	const apiKey = "cb5aa09d0e25d808361008142d94b938";
	
	
	async function getWeather(city){
		const res = await fetch(`${apiUrl}weather?q=${city}&appid=${apiKey}&units=metric&lang=tr`);
		const data = res.json();
		console.log(data);
		return data;
	}

	const setLocation = (e) => {
		if(e.key === "Enter"){
		promise = getWeather(city)
		e.target.value = "";
		} 
	}
	
	let city = "";
	$: promise = "";

</script>



<div class="container">

	<div class="back-home">
		<Link to="/"><i class="fa-solid fa-house"></i></Link>
	</div>

	<div class="search-wrapper">
		<input type="text" 
		bind:value={city} 
		on:keypress={(e) => setLocation(e)} 
		placeholder="Şehir Giriniz">
	</div>

	{#await promise}
	<div class="loader-wrapper">
		<div class="loader"></div>
	</div>
	{:then data} 
		{#if data.name === undefined}
			<p class="warn-message"> Lütfen Geçerli Bir Şehir Adı Girin</p>
		{:else}
			<div class="content-wrapper">
				<div class="content">
					<img src="{`../public/images/${data.weather[0].main}.svg`}" alt="" width="80">
					<div class="content-main">
						<p class="city-degree">{data.main.temp.toString().slice(0,2)}°</p>
						<p class="city-weather-state">{data.weather[0].main}</p>
						<p class="city-title">{data.name}</p>
					</div>

				</div>	
			</div>		
		{/if}

		{:catch error}
		<p>Something went wrong: {error.message}</p>
		
	{/await}


	


</div>



<style>

	.loader-wrapper {
		display: flex;
		justify-content: center;
	}

	.loader {
	border: 16px solid #f3f3f3; /* Light grey */
	border-top: 16px solid #030202; /* Blue */
	border-radius: 50%;
	width: 120px;
	height: 120px;
	animation: spin 2s linear infinite;
	}

	@keyframes spin {
	0% { transform: rotate(0deg); }
	100% { transform: rotate(360deg); }
	}

	.container {
		position: relative;
		width: 100%;
		height: 100vh;
	}

	.back-home {
		display: flex;
		justify-content: center;
		align-items: center;

		position: absolute;
		left: 30px;
		bottom: 30px;
	}
	
	.back-home i {
		display: inline-flex;
		justify-content: center;
		align-items: center;
		background-color: white;
		width: 50px;
		height: 50px;
		font-size: 1.3rem;
		border-radius: 50%;

		transition: .4s ease;
	}

	.back-home i:hover {
		color: white;
		background-color: black;
	}

	.search-wrapper {
		padding: 30px 0;
		text-align: center;
	}

	.search-wrapper input {
		border: none;
		border-bottom: 1px solid white;

		background-color: transparent;
		color: white;

		font-size: 1.2rem;
		font-weight: 600;
		text-align: center;
		padding: 10px 15px;


		transition: all  1s ease;
	}

	.search-wrapper input:focus {
		border-color: yellow;
	}
    .warn-message {
		text-align: center;
		color: white;
	}

	.content-wrapper {
		padding: 0 10px;
		width: 100%;
	}
	.content {
		position: relative;

		display: flex;
		justify-content: space-between;
		flex-direction: row-reverse;

		width: 100%;
		min-width: 220px;
		max-width: 400px;

		margin: 0 auto;
		margin-top: auto;
		padding: 30px 10px;
		background: linear-gradient(90deg, #5936B4 0%, #362A84 103.55%);

		color: white;
		border-radius: 5px;
	}

	.content-main {
		display: flex;
		flex-direction: column;
		gap: 0.3rem;
	}

	.city-title, .city-degree , .city-weather-state {
		margin-left: .5rem;
	}
	.city-degree {
		font-size: 2.5rem;
	}
	.city-weather-state {
		font-size: 1rem;
	}
	.city-title {
		font-size: 2rem;
		font-weight: 600;
	}
</style>



