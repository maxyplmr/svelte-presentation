<main style='{cssVars}'>
    <Title
            title="{title}"
            color={background}
            animationIndex="{animationIndex}"
    ></Title>
    <Board
            title="{title}"
            random="{random}"
            elementsCount="{elements.length}"
            on:addElement={addElement}
            on:removeElement={removeElement}
            on:setColor={setColor}
            on:setAnimation={setAnimation}
            on:setTitle={setTitle}
    ></Board>
    {#each elements as element }
        <Element
                element={element}
                random="{random}"
        ></Element>
    {/each}
</main>

<script>
    const random = (max) => Math.floor(Math.random() * (max - 0 + 1))
    import Element from "./sub-components/Element.svelte"
    import Board from "./sub-components/Board.svelte"
    import Title from "./sub-components/Title.svelte"

    let elements = []
    let background = `rgb(255, 255, 255)`
    let animationIndex = -1
    let title = 'PLMR'

    $:cssVars = `--background: ${ background };`

    function addElement({ detail: element }) {
        elements = [...elements, ...element]
    }

    function removeElement() {
        const [a, b, c, d, e, ...rest] = elements
        elements = rest
    }

    function setColor({ detail: color }) {
        background = color
    }

    function setTitle({ detail: newTitle }) {
        title = newTitle
    }

    function setAnimation() {
        animationIndex = random(16)
    }
</script>

<style>
    main {
        background: var(--background);
        height: 100%;
        width: 100%;
    }
</style>