# Local autosave milestone

One document can now be restored after refreshing the same browser and site.
The footer reports saving, completed saves, and failures. Failed writes expose
retry and draft download; unreadable saved data is preserved for recovery.

## Verification

- Full integrated check: formatting, lint, TypeScript, 59 tests, production build.
- Browser: draft restored after refresh; second-tab editing stopped autosave in
  the first tab; recovery download retained the first tab's document.
- Automated tests cover quota failure and retry, unavailable storage, malformed
  and unsupported records, formatting restoration, lifecycle flushes, and conflicts.

## Boundaries

Storage is local to one browser and origin. It is not a backup or cloud sync.
Clearing site data removes it. Final lifecycle writes are best-effort; two-tab
checks do not provide atomic locking or merging. Document switching, editable
titles, and collaboration remain future work.

Before reverting to a session-only version, download any draft you need to keep.
The previous implementation does not restore the saved record.
