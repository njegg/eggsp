<script>
    export let src = undefined
    export let size = 100
    export let name = 'epik'
    export let id

    let alt = 'icon'
</script>

<div id="icon-{id}" class="icon">
    <img {src} {alt} width={size} height={size}
        draggable={src != undefined}
        on:dragstart
    >

    <span>{name}</span>
</div>

<style>
    .icon {
        width: 100%;
        height: 100%;
    }

    span {
        text-align: center;
        word-wrap: break-word;
    }
</style>