<script>
     import Scroller from "../lib/Scroller.svelte";
     import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <img src ='./house-img.png' alt="cut out paper house" />
        {/snippet}
    
        {#snippet scrolly()}
            <ArticleText>
                
                The effect of redlining has been detrimental on the marginalised groups in America. 
                Since it followed from the 
                
            </ArticleText>
        {/snippet}
    </Scroller>
</div>