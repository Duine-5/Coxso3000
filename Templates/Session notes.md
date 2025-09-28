# Fleeting memory//
> [!quote|mark]  ///
> Do not forget





# - Stat Track -

```dataviewjs
const script = document.createElement("script");
script.src = "https://cdn.plot.ly/plotly-latest.min.js";
script.onload = () => {
    const page = dv.current(); // current session note
    const players = ["Sylphir", "Albertini", "Spooky", "Fanto", "Dario", "Jaeger"];

    const nat20 = players.map(p => Number(page[`${p}_Nat20`] ?? page[p]?.Nat20 ?? 0));
    const nat1  = players.map(p => Number(page[`${p}_Nat1`]  ?? page[p]?.Nat1  ?? 0));

    const trace20 = {
        x: players,
        y: nat20,
        name: "Nat20",
        type: "bar",
        marker: { color: "rgba(251, 70, 72, 0.7)" }
    };

    const trace1 = {
        x: players,
        y: nat1,
        name: "Nat1",
        type: "bar",
        marker: { color: "rgba(0, 255, 245, 0.7)" }
    };

    const layout = {
        title: { text: "Session Stats", font: { color: "#FB4648" } },
        barmode: "group", // side by side
        paper_bgcolor: "#171717",
        plot_bgcolor: "#171717",
        font: { color: "#BABABA" },
        width: 700,
        height: 400,
        xaxis: { title: "Players" },
        yaxis: { title: "Count" }
    };

    Plotly.newPlot(this.container, [trace20, trace1], layout);
};
document.head.appendChild(script);

```

#Session