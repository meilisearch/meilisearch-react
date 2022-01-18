<p align="center">
  <img src="https://raw.githubusercontent.com/meilisearch/integration-guides/main/assets/logos/logo.svg" alt="MeiliSearch-React" width="200" height="200" />
</p>

<h1 align="center">MeiliSearch React</h1>

<h4 align="center">
  <a href="https://github.com/meilisearch/MeiliSearch">MeiliSearch</a> |
  <a href="https://docs.meilisearch.com">Documentation</a> |
  <a href="https://slack.meilisearch.com">Slack</a> |
  <a href="https://roadmap.meilisearch.com/tabs/1-under-consideration">Roadmap</a> |
  <a href="https://www.meilisearch.com">Website</a> |
  <a href="https://docs.meilisearch.com/faq">FAQ</a>
</h4>

<p align="center">
  <a href="https://github.com/meilisearch/meilisearch-react/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-informational" alt="License"></a></p>

<p align="center">⚡ How to integrate a front-end search bar in your React application using MeiliSearch</p>

**MeiliSearch** is an open-source search engine. [Discover what MeiliSearch is!](https://github.com/meilisearch/MeiliSearch)

This repository describes the steps to integrate a relevant front-end search bar with a search-as-you-type experience!

## Installation

To integrate a front-end search bar, you need to install two packages:
- the open-source [React InstantSearch](https://github.com/algolia/react-instantsearch/) library powered by Algolia that provides all the front-end tools you need to highly customize your search bar environment.
- the MeiliSearch client [instant-meilisearch](https://github.com/meilisearch/instant-meilisearch/) to establish the communication between your MeiliSearch instance and the React InstantSearch library.<br>
_Instead of reinventing the wheel, we have opted to reuse the InstantSearch library for our own front-end tooling. We will contribute upstream any improvements that may result from our adoption of InstantSearch._

Run:

```bash
yarn add react-instantsearch-dom @meilisearch/instant-meilisearch
# or
npm install react-instantsearch-dom @meilisearch/instant-meilisearch
```

NB: If you don't have any MeiliSearch instance running and containing your data, you should take a look at this [getting started page](https://docs.meilisearch.com/learn/tutorials/getting_started.html).

## Getting Started

Thanks to the open-source React InstantSearch library, you can add these components to your application:

```js
import React from 'react';
import { InstantSearch, SearchBox, Hits, Highlight } from 'react-instantsearch-dom';
import { instantMeiliSearch } from '@meilisearch/instant-meilisearch';

const searchClient = instantMeiliSearch(
  "https://integration-demos.meilisearch.com",
  "q7QHwGiX841a509c8b05ef29e55f2d94c02c00635f729ccf097a734cbdf7961530f47c47"
);

const App = () => (
  <InstantSearch
    indexName="steam-video-games"
    searchClient={searchClient}
  >
    <SearchBox />
    <Hits hitComponent={Hit} />
  </InstantSearch>
);

const Hit = ({ hit }) => <Highlight attribute="name" hit={hit} />;

export default App
```

🚀 For a full getting started example, please take a look at this CodeSandbox:

[![Edit MS + React-IS](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/ms-react-is-sh9ud?fontsize=14&hidenavigation=1&theme=dark)

💡 If you have never used React InstantSearch before, we recommend reading this [getting started documentation](https://www.algolia.com/doc/guides/building-search-ui/what-is-instantsearch/react/).

## Customization and Documentation

- The open-source React InstantSearch library is widely used and well documented in the [Algolia documentation](https://www.algolia.com/doc/api-reference/widgets/react/). It provides all the widgets to customize and improve your search bar environment in your React application.
- The [instant-meilisearch documentation](https://github.com/meilisearch/instant-meilisearch/) to add some customization.
- The [MeiliSearch documentation](https://docs.meilisearch.com/).

<hr>

**MeiliSearch** provides and maintains many **SDKs and Integration tools** like this one. We want to provide everyone with an **amazing search experience for any kind of project**. If you want to contribute, make suggestions, or just know what's going on right now, visit us in the [integration-guides](https://github.com/meilisearch/integration-guides) repository.
