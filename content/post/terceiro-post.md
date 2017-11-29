---
title: "Eh possivel observar alguma semelhanca no nivel das aguas de boqueirao no mes de junho?"
date: 2017-11-29T20:40:30-03:00
draft: false
---


Olhando o grafico...
<!--more-->

<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
    "$schema": "https://vega.github.io/schema/vega-lite/v3.0.json",
    "data": {
        "url": "https://api.insa.gov.br/reservatorios/12172/monitoramento",
        "format": {
        "type": "json",
        "property": "volumes",
        "parse": {
            "DataInformacao": "utc:'%d/%m/%Y'"
                }
            }
        },
  "mark": "bar",
  "width": 400,
 "transform": [
    {
      "filter": {
        "timeUnit": "year",
        "field": "DataInformacao",
        "range": [
          1994,
          2017
        ]
      }
    },
    {
      "filter": {
        "timeUnit": "month",
        "field": "DataInformacao",
        "range": [
          6,
          7
        ]
      }
    }
  ],
  
"encoding": {
  "x": {
    "timeUnit": "year",
    "field": "DataInformacao",
    "type": "temporal",
    "axis": {"title": "Anos"}
  },
  "y": {
    "aggregate": "mean",
    "field": "VolumePercentual",
    "type": "quantitative",
    "axis": {"title": "M�dia do volume (%)"}
  }
}
};
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>



Nao eh possivel observar semelhancas nos nivel da agua nos meses de junho 