# HTTP response body rewrite example

This example rewrites the JSON response from JSONPlaceholder's public demo endpoint:

`https://jsonplaceholder.typicode.com/todos/1`

The rule matches only that URL. Its MintFlow jq script changes `title` and `completed`, then adds a `mintflowDemo` field. The bundle intentionally omits `priority`, so MintFlow assigns the default priority of `100`.

## Import from URL

In MintFlow, open **HTTP → HTTP Rewrite**, select the toolbar import button, choose **From URL…**, and enter:

```text
https://raw.githubusercontent.com/GalaxNet-Ltd/mintflow-app/main/examples/http-rewrite/jsonplaceholder-response-demo.mfhrb
```

You can instead download [jsonplaceholder-response-demo.mfhrb](jsonplaceholder-response-demo.mfhrb) and choose **Choose File…**. The system file picker can select a local file or one stored in iCloud Drive.

MintFlow imports the script locally and creates the rule disabled. Review the matcher and source, then enable the rule. URL import is a one-time import; MintFlow does not retain or automatically refresh the remote URL.

## Try it

Body rewrite requires MintFlow Pro and working HTTP processing. Make sure the active profile's HTTPS inspection certificate is installed and trusted, TCP port `443` is configured, and either **Capture All** is enabled or `jsonplaceholder.typicode.com` is included in **Domain Capture**. If the client uses HTTP/3, temporarily enabling **Disable HTTP/3** can allow it to fall back to HTTP over TCP.

After applying the profile and connecting, open:

`https://jsonplaceholder.typicode.com/todos/1`

The response should contain these values:

```json
{
  "title": "MintFlow rewrote this JSON response",
  "completed": true,
  "mintflowDemo": "HTTP body rewrite is working"
}
```

Other original fields, including `userId` and `id`, remain unchanged. Disable or remove the example rule after the experiment.

This bundle was checked statically against MintFlow's MFHRB v1 format and bounded MintFlow jq syntax. It was not exercised against live traffic on the publishing Mac.
