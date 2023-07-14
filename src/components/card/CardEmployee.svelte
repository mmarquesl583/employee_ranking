<script>
    let remainingStars;
    let score_class;
    let half_star;
    let fullStars;
    let score;
    let reviews;
    let name = "Matheus Marques Linhares"

    let first = Math.round(Math.random())
    let second = Math.round(Math.random())
    let third = Math.round(Math.random())

    let first_title = `${first} Troféus 1° Lugar`
    let second_title = `${second} Troféus 2° Lugar`
    let third_title = `${third} Troféus 3° Lugar`

    let first_class = "fa-solid fa-trophy"
    let second_class = "fa-solid fa-trophy ml-3 mr-3"
    let third_class = "fa-solid fa-trophy"

    if(first > 0){
        first_class += " text-gold"
    }
    if(second > 0){
        second_class += " text-silver"
    }
    if(third > 0){
        third_class += " text-bronze"
    }

    score = Math.floor(Math.random() * 10) / 2;
    score_class = "ml-3 font-bold text-lg "
    if (score < 3) {
        score_class += "text-red";
    } else if (score <= 4) {
        score_class += "text-yellow";
    } else {
        score_class += "text-green";
    }

    reviews = 3
    score = score.toFixed(1);
    fullStars = Math.floor(score);
    half_star = score % 1 !== 0;
    remainingStars = 5 - fullStars - (half_star ? 1 : 0);
</script>

<div class="b-black card flex">
    <div class="photo b-black"></div>
    <div class="grid ml-3 w-full pr-4">
        <div class="name uppercase font-bold">
            {name}
        </div>
        <div class="mt-auto flex justify-between" >
            <div class="bottom w-28 flex" title={reviews + " Avaliações"}>
                {#each Array.from({ length: fullStars }) as _}
                    <i class="fa-solid fa-star text-yellow-400"></i>
                {/each}
                {#if half_star}
                    <i class="fa-solid fa-star-half-stroke text-yellow-400"></i>
                {/if}
                {#each Array.from({ length: remainingStars }) as _}
                    <i class="fa-regular fa-star text-yellow-400"></i>
                {/each}
                <div class={score_class}>
                        {score}
                </div>
            </div>
            <div class="rewards ml-3">
                <div class="flex">
                    <i title={first_title} class={first_class}></i>
                    <i title={second_title} class={second_class}></i>
                    <i title={third_title} class={third_class}></i>
                </div>
                <div class="flex items-center justify-around mt-1">
                    <i title="X Notas Máximas" class="fa-sharp fa-solid fa-award"></i>
                    <i title="X Notas Mínimas" class="fa-solid fa-thumbs-down"></i>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    i{
        font-size:x-large;
    }
    .b-black{
        border: 1px solid black;
    }
    .card{
        width: 500px;
        height: 120px;
        border-radius: 10px;
        padding: 15px;
    }
    .photo{
        width: 110px;
        height: 90px;
        border-radius: 10px;
    }
    .name{
        height:fit-content
    }
    .text-red{
        color: red;
    }
    .text-yellow{
        color: #cea813
    }
    .text-green{
        color: green;
    }
    .text-gold{
        color: gold;
    }
    .text-silver{
        color: rgb(160, 160, 160);
    }
    .text-bronze{
        color: brown;
    }
    .bottom{
        display: flex;
        align-items: end;
    }
</style>
