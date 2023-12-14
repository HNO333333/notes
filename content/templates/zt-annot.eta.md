---
callout: true
---
<% const bgcolor = {
  "red": "rgba(255, 0, 3, 0.2)",
  "orange": "rgba(255, 140, 0, 0.2)",
  "yellow": "rgba(248, 255, 0, 0.28)",
  "gray": "rgba(92, 92, 92, 0.2)",
  "green": "#d3f8b6",
  "cyan": "rgba(0, 255, 209, 0.28)",
  "blue": "rgba(0, 125, 255, 0.28)",
  "navy": "海军蓝",
  "purple": "rgba(82, 0, 255, 0.28)",
  "brown": "rgba(57, 18, 18, 0.28)",
  "magenta": "rgba(252, 0, 255, 0.28)",
};%>

[!note] [@Page <%= it.pageLabel %>](<%= it.backlink %>)
 <%= it.imgEmbed %>
 <span style="background:<%= bgcolor[it.colorName] %>"><%= it.text %></span><% if (it.comment) { %>
- **Notes**: <%= it.comment %><% } %>