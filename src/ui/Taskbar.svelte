<script>
    const rickroll = (e) => {
        location.href = "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
    }
</script>


<div class="taskbar-container">
    <button id="start-button" on:click={rickroll}>Start</button>
    <span id="taskbar"></span>
    <span id="clock"></span>
</div>


<style>
    .taskbar-container {
        width: 100%;
        height: 40px;
        position: absolute;
        display: flex;
        bottom: 0;
        background-color: var(--taskbar-blue);
    }

    #start-button {
        background-color: var(--start-green);
        width: 10rem;
        margin: 0;
        border: none;
    }

    #taskbar {
        color: black;
        width: 100%;
        border-left: 2px solid rgb(51, 51, 51);
        border-right: 2px solid rgb(51, 51, 51);
    }

    #clock {
        width: 150px;
        background-color: var(--clock-blue);
    }
</style>