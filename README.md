# CRAWLB.IN

!NOTE - the domain used here - _crawlb.in_ is no longer active - references require you to have a functioning domain of your own to test

## Introduction

[crawlbin](https://crawlb.in/) is a service, inspired by [httpbin](http://httpbin.org/) and forked from the original code by Distilled (no longer available as far as I could find), to dynamically create combinations of HTML pages with specific HTTP headers for the purpose of testing crawlers or tools that need to be able to handle potentially misleading signals. You can use crawlbin to deliberately generate pages with technical issues in order to verify how a crawler handles those scenarios.

crawlbin accepts a list of flags in the URL which toggle various directives and HTTP responses. For example, you can simulate a page with a noindex tag, by using the `meta_noindex` flag:

    https://crawlb.in/meta_noindex/
    <meta name=“robots” content=“noindex” />

You can add a (self referencing) canonical tag to the page using the `html_canonical_self` flag:

    https://crawlb.in/html_canonical_self/
    <link rel=“canonical” href=“https://crawlb.in/html_canonical_self/” />

The power of crawlbin comes when you start combining the various flags to allow you to generate the sorts of issues you are likely to encounter when doing any sort of technical audit.

For example, by combining a `response_301` flag with an `html_canonical_next_block` flag, you can simulate a canonical tag that references a page that subsequently 301’s. This is surprisingly common and whilst typically not disastrous, it is something that can and should be fixed. You see this sort of issue with automatic redirects setup to handle things like redirecting http -> https or automatically appending trailing slashes if they don’t exist.

Full documentation is available at [crawlb.in](https://crawlb.in/).

## Contributing

See CONTRIBUTING file.

## License

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License

See LICENSE file.
