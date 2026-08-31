# HTTP response body rewrite examples

These examples rewrite JSON responses from JSONPlaceholder's public demo endpoints:

- `jsonplaceholder-response-demo.mfhrb` uses MintFlow jq on `/todos/1`.
- `jsonplaceholder-response-js-demo.mfhrb` uses JavaScript on `/posts/1`.

The rules use different exact URL matchers, so both examples can be installed at the same time. Both bundles intentionally omit `priority`, so MintFlow assigns the default priority of `100`.

## Import from URL

In MintFlow, open **HTTP → HTTP Rewrite**, select the toolbar import button, choose **From URL…**, and enter one of these addresses.

MintFlow jq example:

```text
https://raw.githubusercontent.com/GalaxNet-Ltd/mintflow-app/main/examples/http-rewrite/jsonplaceholder-response-demo.mfhrb
```

JavaScript example:

```text
https://raw.githubusercontent.com/GalaxNet-Ltd/mintflow-app/main/examples/http-rewrite/jsonplaceholder-response-js-demo.mfhrb
```

You can instead download [the jq bundle](jsonplaceholder-response-demo.mfhrb) or [the JavaScript bundle](jsonplaceholder-response-js-demo.mfhrb) and choose **Choose File…**. The system file picker can select a local file or one stored in iCloud Drive.

MintFlow imports the script locally and creates the rule disabled. Review the matcher and source, then enable the rule. URL import is a one-time import; MintFlow does not retain or automatically refresh the remote URL.

## Prepare HTTP processing

Body rewrite requires MintFlow Pro and working HTTP processing. Make sure the active profile's HTTPS inspection certificate is installed and trusted, TCP port `443` is configured, and either **Capture All** is enabled or `jsonplaceholder.typicode.com` is included in **Domain Capture**. If the client uses HTTP/3, temporarily enabling **Disable HTTP/3** can allow it to fall back to HTTP over TCP.

After enabling an imported rule, apply the profile and connect.

## Try the MintFlow jq example

Open:

`https://jsonplaceholder.typicode.com/todos/1`

The jq script changes `title` and `completed`, then adds `mintflowDemo`. The response should contain:

```json
{
  "title": "MintFlow rewrote this JSON response",
  "completed": true,
  "mintflowDemo": "HTTP body rewrite is working"
}
```

Other original fields, including `userId` and `id`, remain unchanged. Disable or remove the example rule after the experiment.

## Try the JavaScript example

Open:

`https://jsonplaceholder.typicode.com/posts/1`

The JavaScript script changes `title` and adds a marker using MintFlow's read-only request `context`. The response should contain:

```json
{
  "title": "MintFlow JavaScript rewrote this JSON response",
  "mintflowDemo": {
    "language": "JavaScript",
    "method": "GET",
    "working": true
  }
}
```

Other original fields, including `userId`, `id`, and `body`, remain unchanged. Disable or remove the example rule after the experiment.

The bundles were checked statically against MintFlow's MFHRB v1 format and their respective script contracts. They were not exercised against live traffic on the publishing Mac.
