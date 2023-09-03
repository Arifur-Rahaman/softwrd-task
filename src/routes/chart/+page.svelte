<script>
    import { onMount } from "svelte";
    import axios from "axios";
    import PolarAreaChart from "../../components/PolarAreaChart.svelte";
    import Table from "../../components/Table.svelte";
    import { countryDataStore } from "../../store";

    let countries = null;
    const fetchCountries = async () => {
        const res = await axios.get("https://restcountries.com/v3.1/all");
        countryDataStore.set(res.data);
    };

    onMount(() => {
        fetchCountries();
    });
</script>

<div class="bg-[#f4f7ff] grid grid-cols-12 p-11 gap-7">
    <div class="col-start-1 col-end-9">
        <Table />
    </div>
    <div class="col-start-9 col-end-13">
        <PolarAreaChart />
    </div>
</div>

<style lang="postcss">
</style>
