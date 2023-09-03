<script>
    import { goto } from "$app/navigation";
</script>

<div class="min-h-screen flex justify-center items-center">
    <div>
        <h1 class="text-center mb-5 text-2xl font-semibold">Welcome To The Home Page</h1>
        <button class="bg-gray-500 text-gray-50 px-4 py-2 rounded mr-2" on:click={() => goto("/layout")}
            >Navigate To Layout Page</button
        >
        <button class="bg-gray-500 text-gray-50 px-4 py-2 rounded mr-2" on:click={() => goto("/chart")}
            >Navigate To Chart Page</button
        >
        <button class="bg-gray-500 text-gray-50 px-4 py-2 rounded mr-2" on:click={() => goto("/map")}
            >Navigate To Map Page</button
        >
    </div>
</div>

<style lang="postcss">
</style>
