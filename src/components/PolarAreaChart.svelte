<script>
    import { onMount, afterUpdate } from "svelte";
    import { countryDataStore } from "../store";
    import Chart from "chart.js/auto";

    let population;
    let countries = [];

    // Function to update the chart
    function updateChart() {
        if (population) {
            const data = {
                labels: countries.map((country) => country.name.common),
                datasets: [
                    {
                        label: "Population",
                        data: countries.map((country) => country.population),
                        backgroundColor: [
                            "#7b8089",
                            "#9499a1",
                            "#c1c7cd",
                            "#999ea6",
                            "#c1c7cd",
                            "#878d96",
                            "#656c73",
                            "#878d96",
                            "#c1c7cd",
                            "#dde1e6",
                        ],
                        borderWidth: 0,
                    },
                ],
            };
            const config = {
                type: "polarArea",
                data: data,
                options: {
                    responsive: true,
                    cutout: "95%",
                    spacing: 2,
                    scales: {
                        r: {
                            ticks: {
                                display: false, // Hide data values
                            },
                        },
                    },
                    plugins: {
                        legend: {
                            position: "bottom",
                            display: true,
                            labels: {
                                usePointStyle: true,
                                padding: 30,
                                font: {
                                    size: 12,
                                },
                            },
                        },
                        title: {
                            display: false,
                            text: "Countries",
                        },
                    },
                },
            };

            // Destroy the previous chart instance (if it exists)
            if (population.chart) {
                population.chart.destroy();
            }

            // Create a new chart instance
            population.chart = new Chart(population.getContext("2d"), config);
        }
    }

    // Subscribe to changes in the countryDataStore
    countryDataStore.subscribe((value) => {
        countries = [...value]
            .sort((a, b) => b.population - a.population)
            .slice(0, 10);
        // Update the chart when the data changes
        updateChart();
    });

    onMount(() => {
        // Initial chart creation
        updateChart();
    });

    // Update the chart after Svelte updates the DOM
    afterUpdate(() => {
        updateChart();
    });
</script>

<div class="bg-white border border-grey-light rounded pb-4">
    <h6 class="pl-3 py-3 mb-4 border-b border-grey-light font-medium">Countries</h6>
    <canvas bind:this={population} width={400} height={400} />
</div>
