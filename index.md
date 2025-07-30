---
title: RIALTO Homepage
layout: page.njk
---

<div id="publications"></div>

<div id="openaccess"></div>

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
      barcornerradius: 2,
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
      title: {
        text: "Open Access Publication Counts by Year"
      },
      xaxis: {
        title: {
          text: 'Publication Count by OA Category'
        }
      },
      yaxis: {
        title: {
          text: 'Publication Year'
        }
      },
      barmode: 'stack',
      barcornerradius: 2,
    }
  );
}

main();

</script>
