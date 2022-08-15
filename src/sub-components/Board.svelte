<main>
    <div class="board shadow">
        <div class="board__option">
            <div class="board__option-title">Elements:</div>
            <div class="board__option-title">{elementsCount}</div>
        </div>
        <hr>
        <div class="board__option">
            <div class="board__option-title">Element:</div>
            <button on:click={addElement} type="button" class="btn btn-sm btn-dark">+5</button>
            <button on:click={removeElement} type="button" class="btn btn-sm btn-outline-dark">-5</button>
        </div>
        <div class="board__option">
            <div class="board__option-title">Color:</div>
            <button on:click={setColor} type="button" class="btn btn-sm btn-dark">Next</button>
        </div>
        <div class="board__option">
            <div class="board__option-title">Title:</div>
            <input value="{title}" on:keyup={setTitle}/>
        </div>
        <div class="board__option">
            <div class="board__option-title">Animation:</div>
            <button on:click={setAnimation} type="button" class="btn btn-sm btn-dark">Next</button>
        </div>
    </div>
</main>
<script>
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    export let speed;
    export let elementsCount;
    export let random;
    export let title;

    function addElement() {
        const newElements = []
        for (let i = 0; i < 5; i++) newElements.push({background: backgroundGenerator()})
        dispatch('addElement', newElements);
    }

    function removeElement() {
        dispatch('removeElement')
    }

    function setColor() {
        dispatch('setColor', backgroundGenerator());
    }

    function setAnimation() {
        dispatch('setAnimation');
    }

    function setTitle(e) {
        dispatch('setTitle', e.target.value);
    }

    function backgroundGenerator() {
        return `rgb(${random(255)},${random(255)},${random(255)})`
    }

</script>
<style>
    .board {
        padding: 25px;
        width: fit-content;
        margin: 25px;
        border-radius: 10px;
        z-index: 20;
        position: fixed;
        background: white;
    }

    .board__option {
        display: flex;
        gap: 10px;
        align-items: baseline;
    }

    .board__option-title {
        width: 80px;
    }
</style>