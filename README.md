# deluge [![npm](https://img.shields.io/npm/v/@ctrl/deluge.svg?maxAge=3600)](https://www.npmjs.com/package/@ctrl/deluge) [![CircleCI](https://circleci.com/gh/TypeCtrl/deluge.svg?style=svg)](https://circleci.com/gh/TypeCtrl/deluge) [![coverage status](https://codecov.io/gh/typectrl/deluge/branch/master/graph/badge.svg)](https://codecov.io/gh/typectrl/deluge)

> TypeScript api wrapper for [deluge](https://deluge-torrent.org/) using [got](https://github.com/sindresorhus/got)

### Install

```console
npm install @ctrl/deluge
```

### Use

```ts
import { Deluge } from '@ctrl/deluge';

const client = new Deluge({
  baseUrl: 'http://localhost:8112/',
  password: 'deluge',
});

async function main() {
  const res = await client.getAllData();
  console.log(res);
}
```

### API

Docs: https://deluge.netlify.com/  

### Normalized API
These functions have been normalized between torrent clients. Can easily support multiple torrent clients. See below for alternative supported torrent clients

##### getAllData
Returns all torrent data and an array of label objects. Data has been normalized and does not match the output of native `listTorrents()`.

```ts
const data = await client.getAllData();
console.log(data.torrents);
```

##### getTorrent
Returns one torrent data

```ts
const data = await client.getTorrent();
console.log(data);
```

##### pauseTorrent and resumeTorrent
Pause or resume a torrent

```ts
const paused = await client.pauseTorrent();
console.log(paused);
const resumed = await client.resumeTorrent();
console.log(resumed);
```

##### removeTorrent
Remove a torrent. Does not remove data on disk by default.

```ts
// does not remove data on disk
const result = await client.removeTorrent('torrent_id', false);
console.log(result);

// remove data on disk
const res = await client.removeTorrent('torrent_id', true);
console.log(res);
```

### See Also
transmission - https://github.com/TypeCtrl/transmission  
qbittorrent - https://github.com/TypeCtrl/qbittorrent  
utorrent - https://github.com/TypeCtrl/utorrent  
rtorrent - https://github.com/TypeCtrl/rtorrent  
