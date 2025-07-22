<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <img class="big-boom-img" src="vintage-comic-boom" alt="A comic style boom to represent the economic boom" />
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                <strong>
                    Right after the great depression, new establishments constructed to tackle
                    the economic decline frequently took part in a practice called "Redlining"
                </strong>
            </ArticleText>

            <ArticleText>This was the practice of classifying ones race as a risk factor when doing 
                neighbourhood appraisals; leading to a lack of black investment and home ownership.
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .big-boom-img {
        width: 30%;
        margin: 0px auto;
    }
</style>
