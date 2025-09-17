---
Modified: Sep 17, 2025 12:01 PM
---
## - User Trend -
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .sort((a, b) => new Date(a["Session-Date"]) - new 
         Date(b["Session-Date"]))
        .map(p => ({
            date: new Date(p["Session-Date"]),
            sy_n20: Number(p.Duine_Nat20) || 0,
        }));
        
    const dates = data.map(d => d.date)
    const n20 = data.map(d => d.sy_n20)
        
    const trace = {
      x: dates,
      y: n20,
      type: "scatter",
      mode: "lines+markers",
	  marker: {
	  color: "rgba(251, 70, 72, 0.7)", 
      line: { color: "rgba(251, 70, 72, 1)", width: 1 }
	  },
	line: { color: "rgba(251, 70, 72, 0.7)", width: 2 }
    };
    
    const layout = {
	  title: {
      text: "Sylphir",
	  font: { color: "#FB4648" }
	  },
	  paper_bgcolor: "#171717",   // background outside chart
	  plot_bgcolor: "#171717",    // background behind bars
	  font: { color: "#BABABA" }, // axis + labels
	  xaxis: {
        title: "Date",
        type: "date",   // <-- important
        tickformat: "%b %d", // e.g., "Sep 07"
        tickangle: -45,
        standoff: 50
    },
	   yaxis: { title: "Nat20s" }
	};

    Plotly.newPlot(this.container, [trace], layout);
    
};


document.head.appendChild(script);
```
---
## - Historical Best -

![[IMG-Spooky.base#Sy-top]]
## - Historical Worst -
![[IMG-Spooky.base#Sy-low]]
