<script lang="ts">
    type Box = {
        x: number;
        y: number;
        width: number;
        height: number;
    };

    const getOrigin = ({ x, y, width, height }: Box) => {
        const x1 = x;
        const x2 = x + width;

        const y1 = y;
        const y2 = y + height;

        return `${(x1 + x2) / 2}px ${(y1 + y2) / 2}px`;
    };

    const rects: Box[] = [
        { x: 30, width: 20, height: 30, y: 0 },
        { y: 30, width: 30, height: 20, x: 0 },
        { y: 50, width: 30, height: 20, x: 0 },
        { y: 70, width: 30, height: 20, x: 0 },
        { y: 90, width: 30, height: 20, x: 0 },
        { y: 110, width: 30, height: 20, x: 0 },
        { y: 130, width: 30, height: 20, x: 0 },
        { y: 150, width: 30, height: 20, x: 0 },
        { y: 170, width: 30, height: 20, x: 0 },
        { y: 190, width: 30, height: 20, x: 0 },
        { x: 210, y: 30, width: 30, height: 20 },
        { x: 210, y: 50, width: 30, height: 20 },
        { x: 210, y: 70, width: 30, height: 20 },
        { x: 210, y: 90, width: 30, height: 20 },
        { x: 210, y: 110, width: 30, height: 20 },
        { x: 210, y: 130, width: 30, height: 20 },
        { x: 210, y: 150, width: 30, height: 20 },
        { x: 210, y: 170, width: 30, height: 20 },
        { x: 210, y: 190, width: 30, height: 20 },
        { y: 0, x: 50, width: 20, height: 30 },
        { y: 0, x: 70, width: 20, height: 30 },
        { y: 0, x: 90, width: 20, height: 30 },
        { y: 0, x: 110, width: 20, height: 30 },
        { y: 0, x: 130, width: 20, height: 30 },
        { y: 0, x: 150, width: 20, height: 30 },
        { y: 0, x: 170, width: 20, height: 30 },
        { y: 0, x: 190, width: 20, height: 30 },
        { x: 30, y: 210, width: 20, height: 30 },
        { x: 50, y: 210, width: 20, height: 30 },
        { x: 70, y: 210, width: 20, height: 30 },
        { x: 90, y: 210, width: 20, height: 30 },
        { x: 110, y: 210, width: 20, height: 30 },
        { x: 130, y: 210, width: 20, height: 30 },
        { x: 150, y: 210, width: 20, height: 30 },
        { x: 170, y: 210, width: 20, height: 30 },
        { x: 190, y: 210, width: 20, height: 30 },
    ];

    export let scale: number;
    export let x: number;
    export let y: number;
    $: transform = `translate(${x} ${y}) scale(${scale}) `;
    let selected: Box;
</script>

<svg
    width="240"
    height="240"
    viewBox="0 0 240 240"
    {transform}
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
>
    <g clip-path="url(#clip0_202_19)">
        <rect width="240" height="240" fill="white" />
        <rect width="30" height="30" fill="#D9D9D9" />
        <rect x="210" width="30" height="30" fill="#D9D9D9" />
        <rect y="210" width="30" height="30" fill="#D9D9D9" />
        <rect x="210" y="210" width="30" height="30" fill="#D9D9D9" />
        {#each rects as r}
            <rect
                on:mouseenter={() => (selected = r)}
                x={r.x}
                y={r.y}
                width={r.width}
                height={r.height}
                fill="currentColor"
            />
        {/each}
        {#if selected}
            <rect
                x={selected.x}
                y={selected.y}
                width={selected.width}
                height={selected.height}
                fill="currentColor"
            />
        {/if}
    </g>
    <defs>
        <clipPath id="clip0_202_19">
            <rect width="240" height="240" fill="white" />
        </clipPath>
    </defs>
</svg>

<style>
    rect:hover {
        filter: drop-shadow(0px 0px 2px gold);
    }
</style>
