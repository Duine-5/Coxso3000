---
Modified: Sep 15, 2025 5:14 PM
sticker: lucide//dices
---

```dataviewjs
const data = dv.pages('"Entries"')

```
hello

```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .map(p => ({
            date: p["Session-Date"],
            nat20: p.Duine?.Nat20 || 0,
            nat1: p.Duine?.Nat1 || 0
        }));

    const total20 = data.reduce((a,b) => a + b.nat20, 0);
    const total1 = data.reduce((a,b) => a + b.nat1, 0);

    const trace = {
      x: ["Nat20", "Nat1"],
      y: [total20, total1],
      type: "bar"
    };

    Plotly.newPlot(this.container, [trace], { title: "Total rolls for Duine" });
};

document.head.appendChild(script);
```
