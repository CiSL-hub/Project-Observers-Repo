```dataviewjs
const pages = dv.pages();

let nodes = [];
let links = [];

for (let page of pages) {
  nodes.push({
    id: page.file.path,
    label: page.file.name
  });

  if (page.file.outlinks) {
    for (let link of page.file.outlinks) {
      links.push({
        source: page.file.path,
        target: link.path
      });
    }
  }
}

const graph = { nodes, links };

// make sure the folder exists (no errors if it already does)
await app.vault.createFolder("graph").catch(() => {});

// write the graph file
await app.vault.adapter.write(
  "graph/graph.json",
  JSON.stringify(graph, null, 2)
);

// ✨ flavor text ✨
dv.paragraph(`🧠 Nodes: ${nodes.length} • 🔗 Links: ${links.length}`);
dv.paragraph("✅ Graph exported to graph/graph.json");
```
