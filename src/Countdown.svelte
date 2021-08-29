<script>
    import { onMount } from "svelte";

    const second = 1000
    const minute = second * 60
    const hour = minute * 60
    const day = hour * 24

    // function setElementInnerText (id, text) {
    //     const element = document.getElementById(id)
    //     element.innerText = text
    // }

    onMount (()=> {
        const element = document.getElementById(id)
        element.innerText = text

        function countdown() {
            const now = new Date().getTime()
            const singaporeTrip = new Date (`August 19, 2022 23:59:59`).getTime()
            const unixTime = singaporeTrip - now

            setElementInnerText('days', Math.floor(unixTime / day))
            setElementInnerText('hours', Math.floor(unixTime % day / hour))
            setElementInnerText('minutes', Math.floor(unixTime % hour / minute))
            setElementInnerText('seconds', Math.floor(unixTime % minute / second))
        }

        function startTimer(){
            countdown()
            setInterval(countdown, second);
        }

        startTimer()
    })
  
</script>

<h1>Countdown to Singapore Trip Anniversary</h1>
    <div>
        <div class="countdown"><span id="days"></span>days</div>
        <div class="countdown"><span id="hours"></span>hours</div>
        <div class="countdown"><span id="minutes"></span>minutes</div>
        <div class="countdown"><span id="seconds"></span>seconds</div>		
    </div>

<style>
    :global(body){
        background-image: url("https://images.wallpaperscraft.com/image/singapore_casino_hotel_59558_2560x1080.jpg");
        background-size: cover;

    }

    h1 {
        color: aliceblue;
        font-size: 3.5em;
    }
    
    .countdown {
        color: aliceblue;
        display: inline-block;
        font-size: 1.7em;
        padding: 1em;
    }
    
    .countdown span {
        display: block;
        font-size: 5rem;
    }
</style>