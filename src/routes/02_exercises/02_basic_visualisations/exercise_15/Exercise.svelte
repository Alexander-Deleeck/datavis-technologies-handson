<script>
    const width = 100;
    const height = 100;
    const margin = { top: 30, right: 30, bottom: 30, left: 30 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  </script>
  
  <svg {width} {height}>
    <g transform="translate({margin.left}, {margin.top})">
      <rect x=0 y=0 width={innerWidth} height={innerHeight} />
      <circle cx = {innerWidth} cy={innerHeight} r=20 />
    </g>

  </svg>
  
  <style>
    svg {
      border: 1px solid black;
      border-radius: 5px;
    }
    rect {
      fill: yellow;
      opacity: 0.3;
      stroke: aqua;
    }
    circle {
      fill: steelblue;
      opacity: 0.5
    }
  </style>
  