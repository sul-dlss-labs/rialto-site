---
title: RIALTO Homepage
layout: page.njk
---

<div id="publications">
</div>

<div id="openaccess">
</div>

<script>

async function main() {
  publications();
  openaccess();
}

async function publications() {
  const resp = await fetch("data/publications.json");
  let data = await resp.json();

  Plotly.newPlot(
    document.getElementById('publications'),
    data,
    {
      title: {
        text: "Total Publications by Year"
      },
      hovermode: false,
      barcornerradius: 3,
    },
    {
      displaylogo: false
    }
  );
}

async function openaccess() {
  const resp = await fetch("data/openaccess.json");
  let data = await resp.json();

  Plotly.newPlot(
    document.getElementById('openaccess'),
    data,
    {
      height: 500,
      title: {
        text: "Open Access Publication Counts by Year"
      },
      xaxis: {
        title: {
          text: 'Publication Year'
        }
      },
      yaxis: {
        title: {
          text: 'Publication Count by OA Category',
          standoff: 25 
        }
      },
      barmode: 'stack',
      barcornerradius: 3,
    },
    {
      displaylogo: false
    }
  );
}

main();

</script>
