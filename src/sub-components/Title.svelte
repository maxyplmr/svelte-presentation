<div>
    <div class="title animate__animated {currentAnimation}" style='{cssVars}'>{title}</div>
</div>

<script>
    import '../../node_modules/animate.css/animate.css';

    export let title;
    export let animationIndex;
    export let color = `rgb(255, 255, 255)`;

    const listOfAnimation = [
        'animate__bounce',
        'animate__flash',
        'animate__pulse',
        'animate__rubberBand',
        'animate__shakeX',
        'animate__shakeY',
        'animate__headShake',
        'animate__swing',
        'animate__tada',
        'animate__wobble',
        'animate__jello',
        'animate__heartBeat',
        'animate__flip',
        'animate__flipInX',
        'animate__flipInY',
        'animate__flipOutX',
        'animate__flipOutY',
    ]

    $: currentAnimation = listOfAnimation[animationIndex]
    $: cssVars = `--color: ${color};`
</script>

<style>
    .title {
        position: absolute;
        font-size: 150px;
        color: var(--color);
        bottom: 40%;
        left: 0;
        width: 100%;
        text-align: center;
        z-index: 21;
        letter-spacing: 25px;
        filter: invert(1);
        font-family: 'Bangers', cursive;
        animation-iteration-count: infinite;
    }
</style>