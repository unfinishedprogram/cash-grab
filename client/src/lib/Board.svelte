<script lang="ts">
    import ExampleSvg from "../assets/ExampleSvg.svelte";

    let mouseDown = false;
    let zoomAbs = 1000;

    let scale = 1.0;
    let x = 0;
    let y = 0;

    const onMouseMove = (e: MouseEvent) => {
        if (mouseDown) {
            x += e.movementX;
            y += e.movementY;
        }

        x = Math.max(x, -window.innerWidth / 2);
        x = Math.min(x, window.innerWidth / 2);

        y = Math.max(y, -window.innerHeight / 2);
        y = Math.min(y, window.innerHeight / 2);
    };

    const onMouseDown = () => {
        mouseDown = true;
    };
    const onMouseUp = () => {
        mouseDown = false;
    };
    const onMouseLeave = () => {
        mouseDown = false;
    };

    const onScroll = (e: WheelEvent) => {
        zoomAbs = Math.min(Math.max(zoomAbs - e.deltaY, 200), 10000);
        scale = zoomAbs / 1000;
    };
</script>

<div>
    <div class="stats">
        X:{x}
        Y:{y}
        Scale:{scale}
    </div>
    <div
        class="Board"
        on:wheel={onScroll}
        on:mouseleave={onMouseLeave}
        on:mousedown={onMouseDown}
        on:mousemove={onMouseMove}
        on:mouseup={onMouseUp}
    >
        <ExampleSvg {scale} {x} {y} />
    </div>
</div>

<style>
    .stats {
        position: absolute;
        top: 0;
        left: 0;
        background-color: white;
        z-index: 1000;
    }
    .Board {
        max-height: 100vh;
        max-width: 100vw;
    }
</style>
