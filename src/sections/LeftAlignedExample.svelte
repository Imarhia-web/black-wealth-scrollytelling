<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "Group 1",
            data: [
                [1990, 3],
                [2000, 4],
                [2010, 1],
                [2020, 1],
            ],
            color: "#8427c9",
        },
        {
            name: "Group 2",
            data: [
                [1990, 2],
                [2000, 5],
                [2010, -2],
                [2020, 2],
            ],
            color: "#ff99fc",
        },
        {
            name: "Group 3",
            data: [
                [1990, 4],
                [2000, 3],
                [2010, 0],
                [2020, 3],
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = false;

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "Chart Showing Decline in Household Net Worth",
        },
        subtitle: {
            text: "Median household net worth from 2007",
        },
        series: [series[0], series[1]],
    };

    function toggleThirdSeries() {
        const existingSeries = chart.series.find((s) => s.name === "Group 3");

        if (existingSeries) {
            existingSeries.remove();
            thirdSeriesVisible = false;
        } else {
            chart.addSeries(series[2]);
            thirdSeriesVisible = true;
        }
    }
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            <button on:click={toggleThirdSeries} class="toggle-button">
                {thirdSeriesVisible ? "Remove Group 3" : "Add Group 3"}
            </button>
            <div>
                <p>
                    You can use Svelte to add and remove data from a Highcharts
                    chart.
                </p>
                <p>
                    When you click the button above, a third group is toggled in
                    the chart. Check out the source code to see how it's done.
                </p>
                <p>
                    <strong
                        >🤔 How might you use other HTML elements, like
                        checkboxes or radio buttons, in a similar way to filter
                        data?</strong
                    >
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                As recently as 2023, the median net worth for black people 
                is still below $50,000, the way it has been for <strong>16 years</strong>.
            </ArticleText>

            <ArticleText>
                Since 2007, the median networth of households show a steady descrease 
                --accounted for by the 2008 recession-- this took an upward trend towards the mid 2010s. 
            </ArticleText>

            <ArticleText>
               Despite this upward trend, black and hispanic communities remain steadily below the 50k
               mark and there is no significant change for them till the late 2010s.
            </ArticleText>

            
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }

    .toggle-button {
        margin: 20px;
        padding: 20px;
        color: #007052;
        background-color: #0bd956;
        border: solid 2px #007052;
        border-radius: 16px;
        font-size: large;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 0 #007052;
    }

    .toggle-button:active {
        transform: translateY(2px);
        box-shadow: 0 2px 0 #007052;
    }
</style>
