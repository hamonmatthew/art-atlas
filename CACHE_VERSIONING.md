# Art Atlas cache versioning — v17

- All pages that load `artists-curated.js` now use the same content fingerprint: `?v=84fe0cbe4f10`.
- Internal page links include `?v=17-20261118` to request the new document when navigating from updated pages.
- HTML pages include revalidation hints. These are **not** a guarantee against GitHub Pages CDN or browser caching; HTTP response headers control caching.
- When changing `artists-curated.js`, regenerate its content fingerprint in the HTML files. When changing HTML pages, increment the navigation version. This is a static-site solution, not automatic server-side cache invalidation.
- The first visit to an old cached entry page may still serve stale content. A hard refresh can be needed once.
- Visitor submissions continue to use browser localStorage; they are not cleared by these changes.
