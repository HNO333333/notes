[Check at Zotero](<%= it.backlink %>) | <%= it.fileLink %>
<% if (it.abstractNote) { %>
> [!abstract]- ABSTRACT
> <%= it.abstractNote.first().replace(/[\r\n]+/g, " ") %><% } %>

> [!info]- metadata
> - publish date: <% if (it.date) { %><%= it.date %><% } %>
> - title: <%= it.title %>
> - authors: <%= it.authorsShort %>
> - tags: <% for (const $it of it.tags) { %>
> 	- <%= $it %><% } %>
> - url: [find it here](<% if (it.url) { %><%= it.url %> <% } %>)
<%~ include("annots", it.annotations) %>