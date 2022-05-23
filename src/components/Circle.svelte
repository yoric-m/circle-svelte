<script>
  let pos = {};
  let xpx,
    ypx = "";
  let radius = 100;
  let radiuspx = `${radius}px`;
  const newPos = () => {
    pos = {
      x: Math.round(Math.random() * 600),
      y: Math.round(Math.random() * 400),
    };
    xpx = pos.x + "px";
    ypx = pos.y + "px";
    radius = 100 + Math.round(Math.random() * 200);
    radiuspx = `${radius}px`;
    console.log(radiuspx);
  };
  newPos();
  // left = "300px";

  const handleClick = (event) => {
    setTimeout(() => {
      newPos();
    }, 500);
  };
</script>

<div
  on:click={handleClick}
  class="circle"
  style="--xpx:{xpx};--ypx:{ypx};--radiuspx:{radiuspx};"
/>

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
