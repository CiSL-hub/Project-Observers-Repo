<div id="graph" style="width:100%; height:80vh;"></div>

<script src="https://unpkg.com/force-graph"></script>
<script>
fetch("/graph/graph.json")
  .then(r => r.json())
  .then(data => {
    const Graph = ForceGraph()(document.getElementById("graph"))
      .graphData(data)
      .nodeId("id")
      .nodeLabel("label")
      .nodeAutoColorBy("id")
      .linkDirectionalParticles(1)
      .linkDirectionalParticleSpeed(0.002);
  });
</script>
