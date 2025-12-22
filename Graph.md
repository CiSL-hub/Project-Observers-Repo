<div id="graph" style="width:100%; height:80vh; background:#0f0f14;"></div>

<script src="https://unpkg.com/force-graph"></script>

<script>
(async () => {
  const res = await fetch("/graph/graph.json");
  const data = await res.json();

  ForceGraph()(document.getElementById("graph"))
    .graphData(data)
    .nodeId("id")
    .nodeLabel("label")
    .nodeAutoColorBy("id")
    .linkDirectionalParticles(1)
    .linkDirectionalParticleSpeed(0.002)
    .backgroundColor("#0f0f14");
})();
</script>
