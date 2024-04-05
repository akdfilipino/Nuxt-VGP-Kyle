<template>
    
    <v-container>
		<h1>This is the details of {{ name }}</h1>
        <v-table 	theme="dark"
					density="comfortable"
					height="980px"
					fixed-header>
			<thead>
				<tr>
					<th class="text-left">Rocket Name</th>
					<th class="text-left">First Flight Date</th>
					<th class="text-left">Height</th>
					<th class="text-left">Diameter</th>
					<th class="text-left">Mass</th>
                    <th class="text-left">Stages</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="r in getRockets" :key="r.name">
					<td v-if="r.name === name">{{ r.name }}</td>
					<td v-if="r.name === name">{{ convertToDate(r.first_flight, "", [""]) }}</td>
					<td v-if="r.name === name">{{ r.height.meters }}</td>
					<td v-if="r.name === name">{{ r.diameter.meters }}</td>
					<td v-if="r.name === name">{{ r.mass.kg }}</td>
					<td v-if="r.name === name">{{ r.stages }}</td>
				</tr>
			</tbody>
		</v-table>
    </v-container>
</template>

<script setup lang="ts">
	import { useGetRockets } from '#imports';
	import { useConvertToDate } from '#imports';
    const { name } = useRoute().params

    const { rocketsToShow } = await useGetRockets();
    const { convertToDate } = useConvertToDate();

    const getRockets = computed(() => {
        let rocketArray = [...rocketsToShow.value]
        return rocketArray;
    })
</script>