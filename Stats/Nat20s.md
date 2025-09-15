---
Modified: Sep 15, 2025 6:06 PM
---
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .map(p => ({
            date: p["Session-Date"],
            Sy_nat20: p.Duine?.Nat20 || 0,
            Da_nat20: p.Dario?.Nat20 || 0,
            Sp_nat20: p.Spooky?.Nat20 || 0,
            Ja_nat20: p.Jaeger?.Nat20 || 0,
            Al_nat20: p.Albertini?.Nat20 || 0,
            Fa_nat20: p.Fanto?.Nat20 || 0
        }));

    const tot_Sy20 = data.reduce((a,b) => a + b.Sy_nat20, 0);
    const tot_Sp20 = data.reduce((a,b) => a + b.Sp_nat20, 0);
    const tot_Ja20 = data.reduce((a,b) => a + b.Ja_nat20, 0);
    const tot_Fa20 = data.reduce((a,b) => a + b.Fa_nat20, 0);
    const tot_Da20 = data.reduce((a,b) => a + b.Da_nat20, 0);
    const tot_Al20 = data.reduce((a,b) => a + b.Al_nat20, 0);

    const trace = {
      x: ["Sylphir", "Spooky", "Jaeger", "Dario","Fanto", "Albertini"],
      y: [tot_Sy20, tot_Sp20, tot_Ja20, tot_Fa20, tot_Da20, tot_Al20],
      type: "bar"
    };

    Plotly.newPlot(this.container, [trace], { title: "Total Nat20s" });
};

document.head.appendChild(script);
```
