<script>
    import {countryDataStore} from '../store'

    let countries = []
    countryDataStore.subscribe((value)=>{
        countries = value
    })
    //Function to format languages as a comma-separated string
    function formatLanguages(languages) {
        if (languages) {
            return Object.values(languages).join(", ");
        }
        return "-";
    }

    //Function to format currencies
    const formatCurrencies = (currencies)=>{
        if(currencies){
            return Object.keys(currencies).join(", ")
        }
        return '-'
    }
</script>

<table class="w-full table-collapse border border-grey-light">
    <thead>
        <tr>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">Flag</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">Name</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">Population</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">CIOC</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">UN Member Status</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">Currencies (Key)</th>
            <th class="text-sm text-left uppercase font-semibold text-grey-darker p-3 bg-white">Languages</th>
        </tr>
    </thead>
    <tbody class="align-baseline">
        {#each countries as country}
            <tr class="group cursor-pointer hover:bg-gray-100">
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">
                    <img class="h-6 w-10" src={country.flags.png} alt={country.flags.alt} />
                </td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">{country.name.common}</td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">{country.population}</td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">
                    {country.cioc || '-'}
                </td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">
                    {#if country.unMember}
                        <span class="inline-block rounded px-2 py-1 bg-[#acacac] text-[#f2f2f2]">Yes</span>
                        {:else}
                        <span class="inline-block rounded px-2 py-1 bg-[#6c6c6c] text-[#eeeeee]">No</span>
                    {/if}
                </td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">
                    {formatCurrencies(country.currencies)}
                </td>
                <td class="text-sm p-3 border-t border-grey-light whitespace-no-wrap bg-white">{formatLanguages(country.languages)}</td>
            </tr>
        {/each}
    </tbody>
</table>
