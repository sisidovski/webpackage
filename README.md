# Packaging Websites

Not to be confused with [webpack](https://webpack.js.org/), this repository
holds a collection of specifications aimed at packaging websites. These
specifications replace the ~~[W3C TAG's Web Packaging
Draft](https://w3ctag.github.io/packaging-on-the-web/)~~ and will allow people
to bundle together the resources that make up a website, so they can be shared
offline, either with or without a proof that they came from the original
website. A full list of use cases and resulting requirements is available in
[draft-yasskin-wpack-use-cases](https://wicg.github.io/webpackage/draft-yasskin-wpack-use-cases.html)
([IETF
draft](https://tools.ietf.org/html/draft-yasskin-wpack-use-cases)).
The [explainer](explainer.md) walks through how to use these specs to
achieve the use cases.

The specifications come in several layers:

1. [Signed HTTP exchanges (a.k.a. SXG)](https://wicg.github.io/webpackage/draft-yasskin-http-origin-signed-responses.html)
   ([IETF draft](https://tools.ietf.org/html/draft-yasskin-http-origin-signed-responses)):
   These allow a browser to trust that a single HTTP request/response pair was
   generated by the origin it claims.
   * As we implement and test signed exchanges, we're publishing periodic
     snapshots so that browsers, publishers, and intermediates can synchronize
     on the same format. The [current implementation snapshot
     ](https://tools.ietf.org/html/draft-yasskin-httpbis-origin-signed-exchanges-impl)
     is an Internet Draft, and a [draft of the next
     snapshot](https://wicg.github.io/webpackage/draft-yasskin-httpbis-origin-signed-exchanges-impl.html)
     is in this repository.
1. [Web Bundles (previously called Bundled HTTP exchanges)](https://wicg.github.io/webpackage/draft-yasskin-wpack-bundled-exchanges.html)
   ([IETF draft](https://tools.ietf.org/html/draft-yasskin-wpack-bundled-exchanges)):
   A collection of HTTP resources, each of which could be signed or unsigned, with
   some metadata describing how to interpret the bundle as a whole. This
   specification has an initial draft in a PR, but isn't finished yet. This work
   may proceed through either the IETF or the W3C/WHATWG.
1. [Loading](https://wicg.github.io/webpackage/loading.html): A description of
   how browsers load signed and bundled exchanges. This is initially specified
   here, and will eventually merge into the appropriate specs, e.g.
   [Fetch](https://fetch.spec.whatwg.org/), that live in either the W3C or
   WHATWG. Currently this only covers signed exchanges.

A previous draft of the format combined layers 1 and 2 into a single format for
signed packages:
[draft-yasskin-dispatch-web-packaging](https://wicg.github.io/webpackage/draft-yasskin-dispatch-web-packaging.html)
([IETF draft](https://tools.ietf.org/html/draft-yasskin-dispatch-web-packaging)).
The DISPATCH WG at IETF99
[recommended](https://datatracker.ietf.org/doc/minutes-99-dispatch/) the current
split.

## Building this repository

### Building the Draft

Formatted text and HTML versions of the draft can be built using `make`.

```sh
$ make
```

This requires that you have software installed as described in
https://github.com/martinthomson/i-d-template/blob/master/doc/SETUP.md.

### Packaging tools

#### Signed HTTP Exchanges

Install this with `go install github.com/WICG/webpackage/go/signedexchange/cmd/...`.

See [go/signedexchange](go/signedexchange) for the usage of the tool.

#### Bundled HTTP Exchanges

Install this with `go install github.com/WICG/webpackage/go/bundle/cmd/...`.

See [go/bundle](go/bundle) for the usage of the tool.
