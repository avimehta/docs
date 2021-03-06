---
layout: page
title: amp-brightcove
order: 5
---

<!---
Copyright 2015 Brightcove. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->



<table>
  <tr>
    <td width="40%"><strong>Description</strong></td>
    <td>An <code>amp-brightcove</code> component displays the Brightcove Player as used in Brightcove's <a href="https://www.brightcove.com/en/online-video-platform">Video Cloud</a> or <a href="https://www.brightcove.com/en/perform">Perform</a> products.</td>
  </tr>
  <tr>
    <td width="40%"><strong>Availability</strong></td>
    <td>Stable</td>
  </tr>
  <tr>
    <td width="40%"><strong>Required Script</strong></td>
    <td><code>&lt;script async custom-element="amp-brightcove" src="https://cdn.ampproject.org/v0/amp-brightcove-0.1.js">&lt;/script></code></td>
  </tr>
  <tr>
    <td width="40%"><strong>Examples</strong></td>
    <td><a href="https://amp-by-example.appspot.com/amp-brightcove.html">amp-brightcove.html</a><br /><a href="https://github.com/ampproject/amphtml/blob/master/examples/brightcove.amp.html">brightcove.amp.html</a></td>
  </tr>
</table>

The following lists validation errors specific to the `amp-brightcove` tag
(see also `amp-brightcove` in the [AMP validator specification](https://github.com/ampproject/amphtml/blob/master/validator/validator.protoascii)):

<table>
  <tr>
    <th width="40%"><strong>Validation Error</strong></th>
    <th>Description</th>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#tag-required-by-another-tag-is-missing">The 'example1' tag is missing or incorrect, but required by 'example2'.</a></td>
    <td>Error thrown when required <code>amp-brightcove</code> extension <code>.js</code> script tag is missing or incorrect.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#mandatory-attribute-missing">The mandatory attribute 'example1' is missing in tag 'example2'.</a></td>
    <td>Error thrown when <code>data-account</code> attribute is missing.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#implied-layout-isnt-supported-by-amp-tag">The implied layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>Error thrown when implied layout is set to <code>CONTAINER</code>; this layout type isn't supported.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#specified-layout-isnt-supported-by-amp-tag">The specified layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>Error thrown when specified layout is set to <code>CONTAINER</code>; this layout type isn't supported.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#invalid-property-value">The property 'example1' in attribute 'example2' in tag 'example3' is set to 'example4', which is invalid.</a></td>
    <td>Error thrown when invalid value is given for attributes <code>height</code> or <code>width</code>. For example, <code>height=auto</code> triggers this error for all supported layout types, with the exception of <code>NODISPLAY</code>.</td>
  </tr>
</table>

## Example

The `width` and `height` attributes determine the aspect ratio of the player embedded in responsive layouts.

Example:

{% highlight html %}
<amp-brightcove
    data-account="12345"
    data-player="default"
    data-embed="default"
    data-video-id="1234"
    layout="responsive"
    width="480" height="270">
</amp-brightcove>
{% endhighlight %}

## Attributes

**data-account**

The Brightcove Video Cloud or Perform account id.

**data-player** or **data-player-id**

The Brightcove player id. This is a GUID, shortid or "default". The default value is "default".

`data-player` is preferred. `data-player-id` is also supported for backwards-compatibility.

**data-embed**

The Brightcove player id. This is a GUID or "default". The default value and most common value is "default".

**data-video-id**

The Video Cloud video id. Most Video Cloud players will need this.

This is not used for Perform players by default; use it if you have added a plugin that expects a `videoId` param in the query string.

**data-playlist-id**

The Video Cloud playlist id. For AMP HTML uses a video id will normally be used instead. If both a playlist and a video are specified, the playlist takes precedence.

This is not used for Perform players by default; use it if you have added a plugin that expects a `playlistId` param in the query string.

**data-param-***

All `data-param-*` attributes will be added as query parameter to the player iframe src. This may be used to pass custom values through to player plugins, such as ad parameters or video ids for Perform players.

Keys and values will be URI encoded. Keys will be camel cased.

- `data-param-language="de"` becomes `&language=de`
- `data-param-custom-ad-data="key:value;key2:value2"` becomes `&customAdData=key%3Avalue%3Bkey2%3Avalue2`

## Player configuration

This script should be added to the configuration of Brightcove Players used with this component. This allows the AMP document to pause the player. Only the script need be added, no plugin name or JSON are needed.

* http://players.brightcove.net/906043040001/plugins/postmessage_pause.js
