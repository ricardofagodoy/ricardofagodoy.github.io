---
layout: page
title: VPL
permalink: /vpl/
---

<h3>Valor inicial: <input id="inicial" type="text"/></h3>
<h3>Taxa (%): <input id="taxa" type="text"/></h3>
<h3>Valores: <input id="valores" type="text"/></h3>

<input id="calcular" type="button" value="Calcular!" />

<script>

    document.getElementById('calcular').onclick = (event) => {

        const inicial = document.getElementById('inicial').value
        const taxa = document.getElementById('taxa').value/100 + 1
        const valores = document.getElementById('valores').value.split(',')

        let parcelas = 0.00

        for (i = 0; i < valores.length; i++)
            parcelas += (valores[i] / Math.pow(taxa, i + 1))

        const vpl = parcelas - inicial

        alert(vpl.toFixed(3))
    }

</script>
