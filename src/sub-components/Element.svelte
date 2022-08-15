<div>
    <div class="element" style='{cssVars}'></div>
</div>
<script>
    export let element;
    export let random;

    let prevTop = 0
    let prevLeft = 0
    let nextTop = 0
    let nextLeft = 0

    $:cssVars = `
        background: ${element.background};
        --prevTop: ${prevTop}vh; --prevLeft: ${prevLeft}vw;
        --nextTop: ${nextTop}vh; --nextLeft: ${nextLeft}vw;
    `
    setInterval(() => {
        positionSetter()
    }, 1000)

    function positionSetter() {
        prevTop = nextTop
        prevLeft = nextLeft
        nextTop = random(100)
        nextLeft = random(100)
    }
</script>

<style>
    .element {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        position: fixed;
        animation: move 1s ease infinite;
    }

    @keyframes move {
        0% {
            top: var(--prevTop);
            left: var(--prevLeft);
        }
        100% {
            top: var(--nextTop);
            left: var(--nextLeft);
        }
    }
</style>
