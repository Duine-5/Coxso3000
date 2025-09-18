---
Modified: Sep 17, 2025 11:55 AM
---
## - User Trend -
```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";

const player = "Jaeger";

const line2_colour = "96, 33, 192"


script.onload = () => {
    const data = dv.pages('"Entries"')
        .array()
        .sort((a, b) => new Date(a["Session-Date"]) - new 
         Date(b["Session-Date"]))
        .map(p => ({
            date: new Date(p["Session-Date"]),
            dat_n20: Number(p[`${player}_Nat20`]) || 0,
            dat_n1: Number(p[`${player}_Nat1`]) || 0,
        }));
        
    const dates = data.map(d => d.date)
    const n20 = data.map(d => d.dat_n20)
    const n1 = data.map(d => d.dat_n1)
        
    const trace1 = {
      x: dates,
      y: n20, 
      name: "Nat20s",
      type: "scatter",
      mode: "lines+markers",
	  marker: {
	  color: "rgba(251, 70, 72, 0.7)", 
      line: { color: "rgba(251, 70, 72, 1)", width: 1 }
	  },
	line: { color: "rgba(251, 70, 72, 0.7)", width: 2 }
    };
    
    const trace2 = {
      x: dates,
      y: n1, 
      name: "Nat1s",
      type: "scatter",
      mode: "lines+markers",
	  marker: {
	  color: `rgba(${line2_colour}, 0.7)`, 
      line: { color: `rgba(${line2_colour}, 1)`, width: 1 }
	  },
	line: { color: `rgba(${line2_colour}, 0.7)`, width: 2 }
    };
    
    const layout = {
	  title: {
      text: player,
	  font: { color: `rgba(${line2_colour}, 1)`}
	  },
	  paper_bgcolor: "#171717",   // background outside chart
	  plot_bgcolor: "#171717",    // background behind bars
	  font: { color: "#BABABA" }, // axis + labels
	  //width: 800,
	  //height: 300,
	  xaxis: {
        title: "",
        type: "date",   // <-- important
        tickformat: "%b %d", // e.g., "Sep 07"
        tickangle: -45,
        standoff: 50
    },
	   yaxis: { title: "" }
	};

    Plotly.newPlot(this.container, [trace1, trace2], layout);
    
};


document.head.appendChild(script);
```
---
## - Historical Best -

![[IMG-Sylphir.base#F-top]]
## - Historical Worst -
![[IMG-Sylphir.base#F-low]]

