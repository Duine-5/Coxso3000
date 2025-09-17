---
Modified: Sep 17, 2025 3:02 PM
---
# The C0rn3r Of Shame ///
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
    .where(p => p.file.name != "Entries")
        .array()
        .map(p => ({
            date: p["Session-Date"],
            Sy_nat1: Number(p.Duine_Nat1) || 0,
            Da_nat1: Number(p.Dario_Nat1) || 0,
            Sp_nat1: Number(p.Spooky_Nat1) || 0,
            Ja_nat1: Number(p.Jaeger_Nat1) || 0,
            Al_nat1: Number(p.Albertini_Nat1) || 0,
            Fa_nat1: Number(p.Fanto_Nat1) || 0
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
      type: "bar",
      marker: {
	  color: "rgba(251, 70, 72, 0.7)", // cyan with transparency
      line: { color: "rgba(251, 70, 72, 1)", width: 1 }
	  }
    };
    
    const layout = {
	  //title: {
      //text: "Total Nat1s",
	  //font: { color: "#FB4648" }
	  //},
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