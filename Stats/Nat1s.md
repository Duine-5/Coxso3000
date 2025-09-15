---
Modified: Sep 15, 2025 6:05 PM
---
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .map(p => ({
            date: p["Session-Date"],
            Sy_nat1: p.Duine?.Nat1 || 0,
            Da_nat1: p.Dario?.Nat1 || 0,
            Sp_nat1: p.Spooky?.Nat1 || 0,
            Ja_nat1: p.Jaeger?.Nat1 || 0,
            Al_nat1: p.Albertini?.Nat1 || 0,
            Fa_nat1: p.Fanto?.Nat1 || 0
        }));

    const tot_Sy1 = data.reduce((a,b) => a + b.Sy_nat1, 0);
    const tot_Sp1 = data.reduce((a,b) => a + b.Sp_nat1, 0);
    const tot_Ja1 = data.reduce((a,b) => a + b.Ja_nat1, 0);
    const tot_Fa1 = data.reduce((a,b) => a + b.Fa_nat1, 0);
    const tot_Da1 = data.reduce((a,b) => a + b.Da_nat1, 0);
    const tot_Al1 = data.reduce((a,b) => a + b.Al_nat1, 0);

    const trace = {
      x: ["Sylphir", "Spooky", "Jaeger", "Dario","Fanto", "Albertini"],
      y: [tot_Sy1, tot_Sp1, tot_Ja1, tot_Fa1, tot_Da1, tot_Al1],
      type: "bar"
    };

    Plotly.newPlot(this.container, [trace], { title: "Total Nat1s" });
};

document.head.appendChild(script);
```