# AnythingLLM Embedded Chat Widget

**This is a submodule of [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) - the all-in-one AI Application**

**Please report any issues or feature requests to the [main repo](https://github.com/Mintplex-Labs/anything-llm)**

> [!WARNING]
> The core AnythingLLM team publishes a pre-built version of the script that is bundled
> with the main application. You can find [it in the main repo here.](https://github.com/Mintplex-Labs/anything-llm/tree/master/frontend/public/embed)
> You should only be working in this repo if you are wanting to build your own custom embed widget for AnythingLLM

This folder of AnythingLLM contains the source code for how the embedded version of AnythingLLM works to provide a public facing interface of your workspace.

The AnythingLLM Embedded chat widget allows you to expose a workspace and its embedded knowledge base as a chat bubble via a `<script>` or `<iframe>` element that you can embed in a website or HTML.

### Security

- Users will _not_ be able to view or read context snippets like they can in the core AnythingLLM application
- Users are assigned a random session ID that they use to persist a chat session.
- **Recommended** You can limit both the number of chats an embedding can process **and** per-session.

_by using the AnythingLLM embedded chat widget you are responsible for securing and configuration of the embed as to not allow excessive chat model abuse of your instance_

### Developer Setup

- `cd embed` from the root of the repo
- `yarn` to install all dev and script dependencies
- `yarn dev` to boot up an example HTML page to use the chat embed widget.

While in development mode (`yarn dev`) the script will rebuild on any changes to files in the `src` directory. Ensure that the required keys for the development embed are accurate and set.

`yarn build` will compile and minify your build of the script. You can then host and link your built script wherever you like.

## Integrations & Embed Types

### `<script>` tag HTML embed

The primary way of embedding a workspace as a chat widget is via a simple `<script>`

```html
<!--
An example of a script tag embed
REQUIRED data attributes:
  data-embed-id // The unique id of your embed with its default settings
  data-base-api-url // The URL of your anythingLLM instance backend
-->
<script
  data-embed-id="5fc05aaf-2f2c-4c84-87a3-367a4692c1ee"
  data-base-api-url="http://localhost:3001/api/embed"
  src="http://localhost:3000/embed/anythingllm-chat-widget.min.js"
></script>
```

### `<script>` Customization Options

**LLM Overrides**

- `data-prompt` — Override the chat window with a custom system prompt. This is not visible to the user. If undefined it will use the embeds attached workspace system prompt.

- `data-model` — Override the chat model used for responses. This must be a valid model string for your AnythingLLM LLM provider. If unset it will use the embeds attached workspace model selection or the system setting.

- `data-temperature` — Override the chat model temperature. This must be a valid value for your AnythingLLM LLM provider. If unset it will use the embeds attached workspace model temperature or the system setting.

**Style Overrides**

- `data-chat-icon` — The chat bubble icon show when chat is closed. Options are `plus`, `chatBubble`, `support`, `search2`, `search`, `magic`.

- `data-button-color` — The chat bubble background color shown when chat is closed. Value must be hex color code.

- `data-user-bg-color` — The background color of the user chat bubbles when chatting. Value must be hex color code.

- `data-assistant-bg-color` — The background color of the assistant response chat bubbles when chatting. Value must be hex color code.

- `data-brand-image-url` — URL to image that will be show at the top of the chat when chat is open.

- `data-greeting` — Default text message to be shown when chat is opened and no previous message history is found.

- `data-no-sponsor` — Setting this attribute to anything will hide the custom or default sponsor at the bottom of an open chat window.

- `data-sponsor-link` — A clickable link in the sponsor section in the footer of an open chat window.

- `data-sponsor-text` — The text displays in sponsor text in the footer of an open chat window.

- `data-position` - Adjust the positioning of the embed chat widget and open chat button. Default `bottom-right`. Options are `bottom-right`, `bottom-left`, `top-right`, `top-left`.

- `data-assistant-name` - Set the chat assistant name that appears above each chat message. Default `AnythingLLM Chat Assistant`

- `data-assistant-icon` - Set the icon of the chat assistant.

- `data-window-height` - Set the chat window height. **must include CSS suffix:** `px`,`%`,`rem`

- `data-window-width` - Set the chat window width. **must include CSS suffix:** `px`,`%`,`rem`

- `data-text-size` - Set the text size of the chats in pixels.

- `data-username` - A specific readable name or identifier for the client for your reference. Will be shown in AnythingLLM chat logs. If empty it will not be reported.

- `data-default-messages` - A string of comma-separated messages you want to display to the user when the chat widget has no history. Example: `"How are you?, What is so interesting about this project?, Tell me a joke."`

**Behavior Overrides**

- `data-open-on-load` — Once loaded, open the chat as default. It can still be closed by the user. To enable set this attribute to `on`. All other values will be ignored.

- `data-show-thoughts` — Allow users to see the AI's thought process, if applicable, in responses. If set to "false", users will only see a static "Thinking" indication without the explict thought content. If "true" the user will see the full thought content as well as the real response. Defaults to "false".

- `data-support-email` — Shows a support email that the user can used to draft an email via the "three dot" menu in the top right. Option will not appear if it is not set.

### `<iframe>` tag HTML embed

_work in progress_

### `<iframe>` Customization Options

_work in progress_
