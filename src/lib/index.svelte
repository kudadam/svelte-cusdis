<script>
    import { onMount, createEventDispatcher, afterUpdate, onDestroy } from "svelte";
    import { browser } from "$app/env";
    export let attrs;
    export let lang = undefined;

    const dispatch = createEventDispatcher();

    const load = ()=>{
        dispatch("load");
    }

 
    onDestroy(()=>{
        if (browser){
            let url = "https://cusdis.com/js/cusdis.es.js";
            let script  = document.querySelector(`script[src="${url}"]`);
            script.removeEventListener("load", load);
        }
    })

    afterUpdate(async ()=>{
        load();
    })

    onMount(async ()=>{

        if (lang){
            let url = `https://cusdis.com/js/widget/lang/${lang}.js`;
            let langScript = document.querySelector(`script[src="${url}"]`);
            if (!langScript){
                langScript = document.createElement("script");
                langScript.setAttribute("defer",true);
                langScript.src = url;
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
            script.addEventListener("load", load);
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