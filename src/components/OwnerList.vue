<template>
	<div class="ownerList">
		<h1>Owner List</h1>
		<section v-if="errored">An error has occurred.</section>
		<section v-else>
			<div v-if="!searched" class="form-group">
				<label for="searchTerm">Search:</label>
				<input v-model="searchTerm" type="text" class="form-control" placeholder="Last name">
				<button v-on:click="onSearch()">Search</button>
			</div>
			<div v-else>
				<h3>{{ owners.length }}</h3>
				<table class="list">
					<tr>
						<th>Name</th>
						<th>Address</th>
						<th>City</th>
						<th>Telephone</th>
						<th>Pets</th>
					</tr>
					<tr v-for="owner in owners" v-bind:key="owner.id">
						<td>{{ owner.firstName }} {{ owner.lastName }}</td>
						<td>{{ owner.address }}</td>
						<td>{{ owner.city }}</td>
						<td>{{ owner.telephone }}</td>
						<td><ul class="pets">
							<li v-for="pet in owner.pets" class="pet" v-bind:key="pet.id">
								{{ pet.name }}
							</li>
						</ul></td>
					</tr>
				</table>
			</div>
		</section>
	</div>
</template>
<script>
import axios from 'axios'

export default {
	name: 'OwnerList',
	data() {
		return {
			errored: false,
			searchTerm: '',
			searched: false,
			owners: {},
		};
	},
	props: {
		
	},
	methods: {
		onSearch() {
			axios
				.get("http://52.90.76.66:9966/petclinic/api/owners/*/lastname/" + this.searchTerm)
				.then(response => {
					this.owners = response.data;
					console.log(response);
				})
				.catch(error => {
					console.log(error);
					this.errored = true;
				})
				.finally(() => {
					this.searched = true;
				});
		}
	}
}

</script>
