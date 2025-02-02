---
sidebar_label: BrowserContext
---

# BrowserContext class

BrowserContexts provide a way to operate multiple independent browser sessions. When a browser is launched, it has a single BrowserContext used by default. The method [Browser.newPage](./puppeteer.browser.newpage.md) creates a page in the default browser context.

**Signature:**

```typescript
export declare class BrowserContext extends EventEmitter
```

**Extends:** [EventEmitter](./puppeteer.eventemitter.md)

## Remarks

The Browser class extends from Puppeteer's [EventEmitter](./puppeteer.eventemitter.md) class and will emit various events which are documented in the [BrowserContextEmittedEvents](./puppeteer.browsercontextemittedevents.md) enum.

If a page opens another page, e.g. with a `window.open` call, the popup will belong to the parent page's browser context.

Puppeteer allows creation of "incognito" browser contexts with [Browser.createIncognitoBrowserContext](./puppeteer.browser.createincognitobrowsercontext.md) method. "Incognito" browser contexts don't write any browsing data to disk.

The constructor for this class is marked as internal. Third-party code should not call the constructor directly or create subclasses that extend the `BrowserContext` class.

## Example

```ts
// Create a new incognito browser context
const context = await browser.createIncognitoBrowserContext();
// Create a new page inside context.
const page = await context.newPage();
// ... do stuff with page ...
await page.goto('https://example.com');
// Dispose context once it's no longer needed.
await context.close();
```

## Properties

| Property                               | Modifiers             | Type                | Description |
| -------------------------------------- | --------------------- | ------------------- | ----------- |
| [id](./puppeteer.browsercontext.id.md) | <code>readonly</code> | string \| undefined |             |

## Methods

| Method                                                                                        | Modifiers | Description                                                                                                         |
| --------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------- |
| [browser()](./puppeteer.browsercontext.browser.md)                                            |           | The browser this browser context belongs to.                                                                        |
| [clearPermissionOverrides()](./puppeteer.browsercontext.clearpermissionoverrides.md)          |           | Clears all permission overrides for the browser context.                                                            |
| [close()](./puppeteer.browsercontext.close.md)                                                |           | Closes the browser context. All the targets that belong to the browser context will be closed.                      |
| [isIncognito()](./puppeteer.browsercontext.isincognito.md)                                    |           | Returns whether BrowserContext is incognito. The default browser context is the only non-incognito browser context. |
| [newPage()](./puppeteer.browsercontext.newpage.md)                                            |           | Creates a new page in the browser context.                                                                          |
| [overridePermissions(origin, permissions)](./puppeteer.browsercontext.overridepermissions.md) |           |                                                                                                                     |
| [pages()](./puppeteer.browsercontext.pages.md)                                                |           | An array of all pages inside the browser context.                                                                   |
| [targets()](./puppeteer.browsercontext.targets.md)                                            |           | An array of all active targets inside the browser context.                                                          |
| [waitForTarget(predicate, options)](./puppeteer.browsercontext.waitfortarget.md)              |           | This searches for a target in this specific browser context.                                                        |
