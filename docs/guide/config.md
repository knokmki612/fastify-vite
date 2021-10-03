
# Configuration

Most configuration options are covered in the sections relating to them.

Below is a quick reference of all options and their default values.

## General

<table class="infotable">
<tr>
<td width="40%">
<code class="h inline-block">dev</code>
<br>
<br>
<span class="small">Whether or not to run Vite's development server</span>
</td>
<td>
<code><b>process.env.NODE​&lowbar;ENV !== 'production'</b></code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">root</code>
<br><br>
<span class="small">The Vite client app's source root</span>
</td>
<td>
<code><b>process.cwd()</b></code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">renderer</code>
<br><br>
<span class="small"><a href="/internals/renderer-api">Renderer adapter</a></span>
</td>
<td>
<code>No default value</code>
</td>
</tr>
</table>

## Hydration

<table class="infotable">
<tr>
<td width="40%">
<code class="h inline-block">hydration.global</code>
<br><br>
<span class="small"><a href="/guide/global-data">Global Data</a> hydration key</span>
</td>
<td>
<code>'$global'</code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">hydration.payload</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#route-payloads">Route Payload</a> hydration key</span>
</td>
<td>
<code>'$payload'</code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">hydration.payload</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#isomorphic-data">Isomorphic Data</a> hydration key</span>
</td>
<td>
<code>'$data'</code>
</td>
</tr>
</table>

## Deployment

<table class="infotable">
<tr>
<td width="40%">
<code class="h inline-block">build</code>
<br><br>
<span class="small"><a href="/guide/global-data">Global Data</a> hydration key</span>
</td>
<td>
<code>'$global'</code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">generate.enabled</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#route-payloads">Route Payload</a> hydration key</span>
</td>
<td>
<code>process.argv.includes('generate')</code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">generate.server.enabled</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#isomorphic-data">Isomorphic Data</a> hydration key</span>
</td>
<td>
<code>'$data'</code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">generate.server.route</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#isomorphic-data">Isomorphic Data</a> hydration key</span>
</td>
<td>
<code>':url'</code>
</td>
</tr>
</table>

## Vite

As [explained in Vite's documentation](https://vitejs.dev/guide/ssr.html#source-structure), a Vite SSR application requires you to build both a [client](https://vitejs.dev/guide/#index-html-and-project-root) and a [server](https://vitejs.dev/guide/ssr.html#building-for-production) bundle. Since <b>fastify-vite</b> makes your Fastify server recognize `build` and `generate` commands, it also lets you configure <b>client</b> and <b>server</b> entry points. 

::: tip
In plain Vite SSR projects, the server entry point is not something you configure, but rather pass in to Vite's `build` CLI command, while the client entry point is the main JavaScript file you reference from index.html — even though the official documentation refers to index.html as the entry point of your app. This is probably because the generated `index.html` is what is delivered to the browser <b>if you're not performing SSR</b> — but if you are, it gets replaced by what is dynamically generated (SSR) from the server.
:::


<table class="infotable">
<tr>
<td width="40%">
<code class="h inline-block">entry.server</code>
<br><br>
<span class="small">Vite server <a href="/guide/global-data">Global Data</a> hydration key</span>
</td>
<td>
<code>Default value provided by <b>renderer adapter</b></code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">entry.client</code>
<br><br>
<span class="small">Vite <a href="https://vitejs.dev/guide/#index-html-and-project-root">client entry point</a></span>
</td>
<td>
<code>Default value provided by <b>renderer adapter</b></code>
</td>
</tr>
<tr>
<td>
<code class="h inline-block">vite</code>
<br><br>
<span class="small"><a href="/guide/data-fetching.html#isomorphic-data">Isomorphic Data</a> hydration key</span>
</td>
<td>
<code>'$data'</code>
</td>
</tr>
</table>

**fastify-vite** tries to intefere as little as possible in configuring your
Vite apps. 

So if you want to just have `vite.config.js` for all Vite settings,
that will just work as expected. However, you can also use the `vite` key
when passing options to the `fastify.register()` call.


See the internal `options.js` used by <b>fastify-vite</b> [here](https://github.com/terixjs/fastify-vite/blob/main/packages/fastify-vite/options.js).