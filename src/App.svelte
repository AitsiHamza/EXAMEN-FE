<script>
import { onMount } from 'svelte';

	let movies = [];

	onMount(async function() {
		fetch("http://localhost:8000")
		.then((res) => res.json())
		.then((res) => {
			movies = res;
		});
	});
</script>

<main>
<table>
	<thead>
		<tr>
			<th>Titre</th>
			<th>Genres</th>
			<th>Year</th>
		</tr>
	</thead>
		<tbody>
			{#each movies as movie}
				<tr>
					<td>{movie.title}</td>
					<td>{movie.genres.join(', ')}</td>
					<td>{movie.year}</td>
				</tr>
			{/each}
		</tbody>
	</table>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>