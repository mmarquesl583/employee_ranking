<script>
    export let reviews;
    export let second;
    export let score;
    export let first;
    export let third;
    export let name;
    export let max
    export let min

    let remainingStars;
    let half_star;
    let fullStars;

    let first_title = `${first} Troféus 1° Lugar`
    let second_title = `${second} Troféus 2° Lugar`
    let third_title = `${third} Troféus 3° Lugar`

    let max_title = `${max} Notas Máximas`
    let min_title = `${min} Notas Mínimas`

    let score_class = "ml-3 font-bold text-lg scale "

    let first_class = "fa-solid fa-trophy "
    let second_class = "fa-solid fa-trophy ml-3 mr-3"
    let third_class = "fa-solid fa-trophy"

    let max_class = `fa-sharp fa-solid fa-award`
    let min_class = `fa-solid fa-thumbs-up text-blue `

    if(max < 1){
        max_class += " text-green opacity-25"
    }
    if(min > 0){
        min_class += " text-blue opacity-25 "
    }

    if(first > 0){
        first_class += " text-gold"
    }
    else{
        first_class += " text-gold opacity-25"
    }
    if(second > 0){
        second_class += " text-silver"
    }
    else{
        second_class += " text-silver opacity-25"
    }
    if(third > 0){
        third_class += " text-bronze"
    }
    else{
        third_class += " text-bronze opacity-25"
    }

    if(min > 0){
        min_class += " text-blue"
    }
    if(max > 0){
        max_class += " text-green"
    }

    if (score < 3) {
        score_class += "text-red";
    } else if (score <= 4) {
        score_class += "text-yellow";
    } else {
        score_class += "text-green";
    }

    fullStars = Math.floor(score);
    half_star = score % 1 !== 0;
    remainingStars = 5 - fullStars - (half_star ? 1 : 0);
</script>

<div class="b-black card flex shadow-xl">
        <i class="photo b-black fa-solid fa-user flex items-end justify-center "></i>
    <div class="grid ml-3 w-full pr-4">
        <div class="name uppercase font-bold">
            {name}
        </div>
        <div class="mt-auto flex justify-between" >
            <div class="bottom w-28 flex" title={reviews + " Avaliações"}>
                {#each Array.from({ length: fullStars }) as _}
                    <i class="fa-solid fa-star text-yellow-400 "></i>
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
                    <i title={max_title} class={max_class}></i>
                    <i title={min_title} class={min_class}></i>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    i{
        font-size:x-large;
    }
    i:hover, .scale:hover{
        cursor: pointer;
        --tw-scale-x: 1.15;
        --tw-scale-y: 1.15;
        transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
    }
    .b-black{
        border: 1px solid black;
    }
    .card{
        width: 500px;
        height: 120px;
        border-radius: 10px;
        padding: 15px;
        margin-bottom: 10px;
        background-color: white;
    }
    .photo{
        width: 110px;
        height: 90px;
        border-radius: 10px;
        font-size: 60pt
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
        color: rgb(255, 187, 0);
    }
    .text-silver{
        color: rgb(160, 160, 160);
    }
    .text-bronze{
        color: brown;
    }
    .text-blue{
        color: rgb(0, 108, 197);
    }
    .bottom{
        display: flex;
        align-items: end;
    }
</style>
