# Svelte Cusdis

This is Cusdis integration for Svelte. Cusdis is a new lightweight, privacy first, open-source commenting system.

## Installation

You can install Svelte Cusdis with `npm` or `yarn`.

```
npm i svelte-cusdis
```

## Usage

```svelte
<script>
	import Cusdis from "svelte-cusdis";
</script>

<Cusdis
 attrs = {{
	 appId: "2f49c941-a723-4350-a9eb-cad6fab4772b",
	 pageId: "1",
	 pageUrl: "https:localhost:3000",
	 pageTitle: "Svelte Cusdis"
 }}
/>
```

## Props

Props refer to the data that the component might need.

| Property | Type | Description | Required |
|-----------|-----|-------------|------------|
| lang | String | This is used to set the language. You need to enter the language code | No |
| attrs.appId | String | The website ID. This can be found on the dashboard | Yes |
| attrs.host | String | API server host. Default is cusdis, You should change it to your host if you self host Cusdis.| No |
| attrs.pageId | String | Current page ID. Used to identity your page. Should be unique in a website. Such as page slug, permalink.| Yes|
|attrs.pageUrl | String | Current page URL. Used to display on dashboard.| No |
| attrs.pageTitle | String | Current page title. Used to display on dashboard. | No |
| attrs.theme | String | Used to set the theme of the app. Values are light, dark and auto | No |
