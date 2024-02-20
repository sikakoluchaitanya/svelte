<script>
    import { scaleSequential, interpolateRainbow} from 'd3';
    import { layoutPhyllotaxis } from "./utils";
    const data = layoutPhyllotaxis(Array.from({ length:1000}));
    const colorGenerator = scaleSequential([0, data.length -1],interpolateRainbow);
</script>

<main>
    <svg viewBox="0 0 100 100">
        <g>
            {#each data as { x, y, r}, i}
            <circle
                cx={x}
                cy={y}
                r={r}
                fill={colorGenerator(i)}
            />
            {/each}
        </g>
    </svg>
</main>

<style>
    main{
        width: 100vw;
        height: 100vh;
        background:  radial-gradient(rgb(0,0,0),rgb(60,60,60));
    }

    svg{
        width: 100%;
        height: 100%;
    }

    g{
        transform: translate(50%, 50%);
    }

</style>
