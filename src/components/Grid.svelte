<script>
    import Icon from "./Icon.svelte";
    import {onMount} from 'svelte'

    export let n = 16
    export let m = 9

    export let icons = []

    let hoveringId = undefined
    let draggingId = undefined

    let grid
    onMount(() => {
        grid.style.gridTemplateColumns = `repeat(${n}, ${cellSizePx}px`
        grid.style.gridTemplateRows = `repeat(${m}, ${cellSizePx}px`
    })


    function drag(event, id) {
        draggingId = id
	}
	
	function drop(event) {
        
        let fromId = draggingId
        console.log('dropping from ' + fromId + ' to ' + hoveringId)

        if (!icons[hoveringId]) {
            let cell = document.getElementById('cell-' + hoveringId)
            let icon = document.getElementById('icon-' + fromId)
            cell.appendChild(icon)

            icons[hoveringId] = icons[fromId]
            icons[fromId] = undefined
        }

        console.log(icons)

        draggingId = hoveringId = undefined
	}

    const hover = (event, id) => {
        event.preventDefault()
        hoveringId = id
    }

    let cellSizePx = 75
    let imageSizePx = cellSizePx * 0.8
</script>

<div id="grid" bind:this={grid} >
    {#each { length: m * n } as _, id} 
        <div class="cell"
             id="cell-{id}"
             on:dragover={e => hover(e, id)}
             on:drop={e => e.preventDefault()}
             on:dragend={drop}
        >
            {#if icons[id]}
                <Icon {id}
                      src={icons[id].src} 
                      size={imageSizePx}
                      on:dragstart={e => drag(e, id)}
                ></Icon>
            {/if}
        </div>
    {/each}
</div>


<style>
    #grid {
        display: grid;
    }

    .cell {
        /* border: 1px solid gray; */
        font-size: 10px;
        text-align: center;
    }
</style>
