# Rafiki documentation

This repo is the code behind [rafiki.dev](https://rafiki.dev), our documentation website for Rafiki.

## Contribute

This website is built with [Starlight](https://starlight.astro.build/), a documentation framework based on [Astro](https://astro.build/).

### Local Development

- Make sure all the dependencies for the website are installed:

```sh
$ pnpm i
```

- Run the dev server:

```sh
$ pnpm start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

- Build the site:

```sh
$ pnpm build
```

This command generates static content into the build directory and can be served using any static contents hosting service.

## Editing Content

Due to the nature of how Starlight deals with content and their generated URLs, all docs content lives in `/src/content/docs/`. For example, the home page of the documentation lives within the `/src/content/docs/` folder and is rendered at rafiki.dev, not rafiki.dev/docs.

### Editing an existing docs page

Edit docs by navigating to `/src/content/docs` and editing the corresponding document:

`/src/content/docs/RELEVANT_FOLDER/doc-to-be-edited.md`

```markdown
---
title: This Doc Needs To Be Edited
---

Edit me...
```

Refer to the Starlight documentation on [authoring content](https://starlight.astro.build/guides/authoring-content/) for more detailed guidance.

### Docs components

We have extracted some of the commonly repeated patterns within the documentation pages into custom docs components that can be reused.

- [CodeBlock](#codeblock-component)
- [Disclosure](#disclosure-component)
- [Hidden](#hidden-component)
- [LargeImg](#largeimg-component)
- [LinkOut](#linkout-component)
- [StylishHeader](#stylishheader-component)
- [Tooltip](#tooltip-component)

1. #### `CodeBlock` component

   Use this component if you wish to add a title to your code block. It takes a `title` attribute, which will be displayed above the code. To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `CodeBlock` component like so:

   ```
   import CodeBlock from '/src/components/docs/CodeBlock'
   ```

   Use the `<CodeBlock>` component within your content like so:

   ````
   <CodeBlock title="Response">

   ```http
   {
      "id":"https://wallet.example/alice/incoming-payments/08394f02-7b7b-45e2-b645-51d04e7c330c",
      "paymentPointer":"https://wallet.example/alice",
      "receivedAmount": {
         "value":"0",
         "assetCode":"USD",
         "assetScale":2
      },
      "completed":false,
      "createdAt":"2022-03-12T23:20:50.52Z",
      "updatedAt":"2022-03-12T23:20:50.52Z",
   }
   ```

   </CodeBlock>
   ````

1. #### `Disclosure` component

   Use this component if you have some content that you want to show/hide via a collapsible container. This component wraps around whatever content you wish to have this expand/collapse behaviour. Note that the `client:load` attribute is required for the functionality to work because this component relies on state.

   To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `Disclosure` component like so:

   ```jsx
   import Disclosure from '/src/components/docs/Disclosure'
   ```

   Use the `<Disclosure>` component within your content like so:

   ```jsx
   <Disclosure toggleText='Show code snippets' client:load>
      <!-- Your content, can be markup or markdown -->
   </Disclosure>
   ```

   For the specific use-case of displaying multiple code-snippets, it might be worth considering also using the [built-in Starlight `<Tabs>`](https://starlight.astro.build/guides/components#tabs) component:

   ````jsx
   <Disclosure toggleText='Show code snippets' client:load>
      <Tabs>
         <TabItem label='Request'>
         ```bash
         GET /alice HTTP/1.1
         Accept: application/json
         Host: wallet.example
         ```
         </TabItem>
         <TabItem label='Response'>
         ```bash
         HTTP/1.1 200 Success
         Content-Type: application/json

         {
            "id":"https://wallet.example/alice",
            "assetCode":"USD",
            "assetScale":2,
            "authServer":"https://wallet.example/auth",
         }
         ```
         </TabItem>

      </Tabs>
   </Disclosure>
   ````

1. #### `Hidden` component

   Use this component to hide content that is temporarily not ready to be shown to the public. This is not meant for long-term use, but a stop-gap when the current implementation is still far away from our documentation/specifications, and the content we have will be relevant but in the future.

   Unfortunately, due to the nature of how the ToC on the right is generated, if we want to hide an entire section (including the header), we will have to manually hide the section heading by either commenting it out or deleting it.

1. #### `LargeImg` component

   Use this component if you have a diagram or image that is much larger than our available space and you would like users to view the full image in another tab. This adds a link to "View full image" with an external link indicator on the bottom right corner under the image. It takes in a `src` and `alt`, just like a normal `img` element.

   To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `LargeImg` component like so:

   ```jsx
   import LargeImg from '/src/components/docs/LargeImg'
   ```

   Use the `<LargeImg>` component within your content like so:

   ```jsx
   <LargeImg src='/img/OMG_A_GIGANTIC_IMG.png' alt='A really large diagram' />
   ```

   For user doc diagrams, be sure to include the `docs` folder in the path.

   ```jsx
   <LargeImg
     src='/img/docs/OMG_A_GIGANTIC_IMG.png'
     alt='A really large diagram'
   />
   ```

1. #### `LinkOut` component

   Use this component if you need to add an external link to your content that opens in a new tab. This component adds the necessary attributes for external links and adds an external link indicator icon to the end of the link content. The icon can be turned off, if necessary.

   To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `LinkOut` component like so:

   ```jsx
   import LinkOut from '/src/components/docs/LinkOut'
   ```

   Use the `<LinkOut>` component within your content like so:

   ```jsx
   <LinkOut href='https://openpayments.guide/'>OpenPayments API</LinkOut>
   ```

   If you do not want the external link icon to appear, you can set the `withIcon` prop to `false` like so:

   ```jsx
   <LinkOut href='https://openpayments.guide/' withIcon={false}>
     OpenPayments API
   </LinkOut>
   ```

1. #### `StylishHeader` component

   Use this component if you wish to create a stylized heading that does not use the heading elements such that it will not appear in the ToC right sidebar. To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `StylishHeader` component like so:

   ```jsx
   import StylishHeader from '/src/components/docs/StylishHeader'
   ```

   Use the `<StylishHeader>` component within your content like so:

   ```jsx
   <StylishHeader>Wow I'm a stylish header</StylishHeader>
   ```

1. #### `Tooltip` component

   Use the tooltip component for adding a short explanation to specific terms. This component is built to be accessible in accordance to the guidance from [WAI Tooltip Pattern](https://www.w3.org/WAI/ARIA/apg/patterns/tooltip/). Note that the `client:load` attribute is required for the functionality to work because this component relies on state.

   To use it, your docs page must be in `.mdx` format. Please change the format from `.md` to `.mdx` if necessary. All your existing markdown will still be supported without issue. Import the `Tooltip` component like so:

   ```jsx
   import Tooltip from '/src/components/docs/Tooltip'
   ```

   Use the `<Tooltip>` component within your content like so:

   ```jsx
   <Tooltip content='THIS CONTENT IS DISPLAYED IN THE TOOLTIP UPON INTERACTION' client:load><span>text that you are trying to explain</span></Tooltip>.
   ```

   If the text you are trying to explain is also a link to somewhere else, please put the link within the `<Tooltip>` like so:

   ```jsx
   <Tooltip content='THIS CONTENT IS DISPLAYED IN THE TOOLTIP UPON INTERACTION' client:load><a href="/URL">text that you are trying to explain</a></Tooltip>.
   ```

## Adding Content

### Adding a new docs page to an existing sidebar

1. Create the doc as a new markdown file in `/src/content/docs/RELEVANT_FOLDER`, example
   `/src/content/docs/RELEVANT_FOLDER/newly-created-doc.md`:

```md
---
title: This Doc Needs To Be Written
---

My new content here..
```

The sidebar of the documentation site is configured in the `astro.config.mjs`.

```javascript
// Add newly-created-doc to the Getting Started category of docs
{
  "docs": {
    "Getting Started": [
      "quick-start",
      "newly-created-doc" // new doc here
    ],
    ...
  },
  ...
}
```

Refer to the Starlight documentation on [sidebar configuration](https://starlight.astro.build/reference/configuration/#sidebar/) for more detailed guidance.

### Adding custom pages

Astro is a content-focused web framework that integrates with a lot of existing framework libraries, making it relatively flexible for building customised sites.

Pages exist in the `/src/pages` directory, and out-of-the-box come with absolutely nothing. For the web monetization website, we have created custom layout components that form the frame of a basic HTML web page, and allow you to add content that would populate the `main` element of the page via a concept known as [slots](https://docs.astro.build/en/core-concepts/astro-components/#slots). A `<slot />` allows you to specify where individual page content should be injected.

```
---
import i18next, { t, changeLanguage } from "i18next";
import Base from '../layouts/Base.astro';
---
<Base>
  /* Page content goes here */
</Base>

```

Refer to the Astro documentation on [pages](https://docs.astro.build/en/core-concepts/astro-pages/) for more detailed guidance.
