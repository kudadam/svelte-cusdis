<script>
    import { onMount } from "svelte";
     export let attrs;
    export let lang = undefined;

    onMount(async ()=>{


        if (lang){
            let langScript = document.querySelector(`script[src="${lang}"]`);
            if (!langScript){
                langScript = document.createElement("script");
                langScript.setAttribute("defer",true);
                langScript.setAttribute("async",true);
                document.querySelector("head").appendChild(langScript);
            }
        }

        let url = "https://cusdis.com/js/cusdis.es.js";
        let script  = document.querySelector(`script[src="${url}"]`);
        if (!script){
            script = document.createElement("script");
            script.src = url;
            script.defer = true;
            script.async = true;
            document.querySelector("head").appendChild(script);
        }
    })
</script>

<div
id = "cusdis_thread"
data-host = {attrs.host || "https://cusdis.com"}
data-app-id = {attrs.appId}
data-page-id = {attrs.pageId}
data-page-url = {attrs.Url}
data-page-title = {attrs.pageTitle} 
data-theme = {attrs.theme}
/>