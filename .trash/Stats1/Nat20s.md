---
Modified: Sep 16, 2025 6:06 PM
---
# The H4ll of Fame ///
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .map(p => ({
            date: p["Session-Date"],
            Sy_nat20: Number(p.Duine_Nat20) || 0,
            Da_nat20: Number(p.Dario_Nat20) || 0,
            Sp_nat20: Number(p.Spooky_Nat20) || 0,
            Ja_nat20: Number(p.Jaeger_Nat20) || 0,
            Al_nat20: Number(p.Albertini_Nat20) || 0,
            Fa_nat20: Number(p.Fanto_Nat20) || 0
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
      type: "bar",
	  marker: {
	  color: "rgba(251, 70, 72, 0.7)", // cyan with transparency
      line: { color: "rgba(251, 70, 72, 1)", width: 1 }
	  }
    };
    
    const layout = {
	  title: {
      text: "Total Nat20s",
	  font: { color: "#FB4648" }
	  },
	  paper_bgcolor: "#171717",   // background outside chart
	  plot_bgcolor: "#171717",    // background behind bars
	  font: { color: "#BABABA" }, // axis + labels
	  width: 800,
	  height: 300
	};

    Plotly.newPlot(this.container, [trace], layout);
    
};


document.head.appendChild(script);
```
---