## ♡ Tidy URL

A Node Package & Userscript that removes tracking or garbage parameters from URLs making them shorter, cleaner and a lot nicer to read.

[![NPM](https://img.shields.io/npm/v/tidy-url)](https://www.npmjs.com/package/tidy-url)
[![NPM](https://img.shields.io/npm/dt/tidy-url)](https://www.npmjs.com/package/tidy-url)
[![NPM](https://img.shields.io/npm/types/tidy-url)](https://www.npmjs.com/package/tidy-url)

## Install

Want this to automatically work in the browser? Click [here](https://github.com/DrKain/tidy-url/wiki/Userscript) to see how!  
If not, the NodeJS guide is below. More information in the [wiki](https://github.com/DrKain/tidy-url/wiki).

```
npm install tidy-url
```

### Require

```js
import { TidyURL } from 'tidy-url';
// or
const { TidyURL } = require('tidy-url');
```

### Usage

Then pass it a URL and let the magic happen:

```js
const link = TidyURL.clean('https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih?si=-k8RwDQwTCK923jxZuy07w&utm_source=copy-link');
console.log(link.url); // https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih
```

### Validating

You can validate a URL using the `validate` function.

```js
TidyURL.validate('https://example.com'); // true
TidyURL.validate('cat'); // false
```

### Note

You will always receive a valid response, even if nothing was modified. For example:  
```js
const link = TidyURL.clean('https://duckduckgo.com/this-is-fine');

link.url; // https://duckduckgo.com/this-is-fine
link.info.reduction; // 0 (percent)
```

### Supported Sites

You can view all custom supported sites [here](https://github.com/DrKain/tidy-url/wiki/Supported-Sites).  
However, the global rules will be enough to work with thousands of sites around the internet. You should be able to pass any URL for cleaning.  
Request direct support for a website [here](https://github.com/DrKain/tidy-url/issues/new?assignees=&labels=&template=add-website.md&title=Website%3A+example.com)

### Response

The response will always be an object with details of what was cleaned or modified in the URL.  
This can be used for debugging, testing or a simple way of letting users know they could have sent a shorter link.

```
{
  url: 'https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih',
  info: {
    original: 'https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih?si=-k8RwDQwTCK923jxZuy07w&utm_source=copy-link',
    reduction: 47,
    replace: [],
    remove: [
      'ga_source',    'ga_medium',
      'ga_term',      'ga_content',
      'ga_campaign',  'ga_place',
      'utm_campaign', 'utm_source',
      'utm_medium',   'utm_content',
      'utm_term',     'gclid',
      'gclsrc',       'si',
      'utm_source',   'context'
    ],
    match: [ [Object], [Object] ],
    custom: false
  }
}
```

### Example

Turn these monstrosities:

```
https://poetsroad.bandcamp.com/?from=search&search_item_id=1141951669&search_item_type=b&search_match_part=%3F&search_page_id=1748155363&search_page_no=1&search_rank=1&search_sig=a9a9cbdfc454df7c2999f097dc8a216b

https://www.audible.com/pd/Project-Hail-Mary-Audiobook/B08G9PRS1K?plink=GZIIiCHG0Uo5V8ND&ref=a_hp_c9_adblp13nmpxxp13n-mpl-dt-c_1_2&pf_rd_p=164101a8-2aab-4c5e-91ee-1f39e10719e6&pf_rd_r=2Q5R6VH8HJAD48PSQRS4

https://www.amazon.com/Alexander-Theatre-Sessions-Poets-Fall/dp/B08NT852YT/ref=sr_1_1?dchild=1&keywords=Poets+of+the+fall&qid=1621684985&sr=8-1

https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih?si=-k8RwDQwTCK923jxZuy07w&utm_source=copy-link

https://www.aliexpress.com/item/1005001913861188.html?spm=a2g0o.productlist.0.0.b1c55e86sFKsxH&algo_pvid=b4648621-2371-4d1e-9a9c-89b4d6c59395&algo_expid=b4648621-2371-4d1e-9a9c-89b4d6c59395-0&btsid=0b0a556816216865399393168e562d&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_

https://www.google.com/search?q=cat&source=hp&ei=AwGpYKzyE7uW4-EPy_CnSA&iflsig=AINFCbYAAAAAYKkPE4rmSi0Im0sHgmOVb3DYosyq2B0B&oq=cat&gs_lcp=Cgdnd3Mtd2l6EAMyBQguEJMCMgIILjICCAAyAggAMgIILjICCAAyAggAMgIILjICCC4yAgguOggIABDqAhCPAToLCC4QxwEQowIQkwI6CAguEMcBEKMCUNgEWIQHYMwIaAFwAHgAgAHIAYgB2ASSAQMyLTOYAQCgAQGqAQdnd3Mtd2l6sAEK&sclient=gws-wiz&ved=0ahUKEwjs_9PdrN3wAhU7yzgGHUv4CQkQ4dUDCAY&uact=5
```

Into these:

```
https://poetsroad.bandcamp.com/

https://www.audible.com/pd/Project-Hail-Mary-Audiobook/B08G9PRS1K

https://www.amazon.com/Alexander-Theatre-Sessions-Poets-Fall/dp/B08NT852YT

https://open.spotify.com/track/1hhZQVLXpg10ySFQFxGbih

https://www.aliexpress.com/item/1005001913861188.html

https://www.google.com/search?q=cat
```

## 🤝 Contributing

Contributions, issues and feature requests are welcome!
Feel free to check [issues page](https://github.com/DrKain/tidy-url/issues).

## 👤 Author

This project was made by **Kain (ksir.pw)**
Feel free to contact me if you have any trouble with this package.

-   Website: [ksir.pw](https://ksir.pw)
-   Github: [@DrKain](https://github.com/DrKain)
-   Discord: Kain#6880

