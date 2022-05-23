<script>
  let pos = {};
  let xpx,
    ypx = "";
  let radius = 100;
  let radiuspx = `${radius}px`;
  let hit = false;
  let width;
  let height;
  const elt = document.querySelector(".hit");
  const newPos = () => {
    //elt.style.display = "none";
    radius = 100 + Math.round(Math.random() * 200);
    pos = {
      x: Math.round(Math.random() * (width - radius * 2)),
      y: Math.round(Math.random() * (height - radius * 2)),
    };
    xpx = pos.x + "px";
    ypx = pos.y + "px";
    radiuspx = `${radius}px`;
    hit = false;
  };
  newPos();
  // left = "300px";

  const handleClick = (event) => {
    hit = true;
    const elt = document.querySelector("#clc");

    elt.classList.add("hit");
    elt.style.left = event.x - 0 + "px";
    elt.style.top = event.y - 0 + "px";
    elt.style.display = "block";
    //elt.classList.remove("run-animation");
    //void elt.offsetWidth;

    setTimeout(() => {
      elt.style.display = "none";
      newPos();
    }, 1000);
  };
</script>

<svelte:window bind:innerWidth={width} bind:innerHeight={height} />
<div
  on:click={handleClick}
  class="circle "
  style="--xpx:{xpx};--ypx:{ypx};--radiuspx:{radiuspx};"
>
  <div id="clc" />
</div>

<style>
  .circle {
    border-radius: 50%;
    border: 1px solid black;
    position: absolute;
    left: var(--xpx);
    top: var(--ypx);
    width: var(--radiuspx);
    height: var(--radiuspx);
    cursor: crosshair;
  }
</style>
