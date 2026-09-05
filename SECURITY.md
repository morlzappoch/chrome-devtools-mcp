## Security policy

The Chrome DevTools MCP project takes security very seriously. Please use [Google Open Source Software Vulnerability Reward Program](https://bughunters.google.com/about/rules/open-source/google-open-source-software-vulnerability-reward-program-rules) to report any security issues.

### Scope

In general, it is the expectation that the AI agent or client using this MCP server validates any input (including tool calls and parameters) before sending it. The server provides powerful capabilities for browser automation and inspection, and it is the responsibility of the calling agent to ensure these are used safely and as intended.

Several tools in this project have the ability to perform actions such as writing files to disk (e.g., via browser downloads or screenshots), loading source maps, or dynamically loading Chrome extensions. These are intentional, documented features and are not vulnerabilities.

The server returns web content to the client as text (Markdown-like) or
structured data (`--experimentalStructuredContent`). The web content is returned
as-is to facilitate debugging and we do not consider changes in the output
text/Markdown structure based on the web content to be vulnerabilities. If
structure is important for your use case, use structured output
(`--experimentalStructuredContent`). Prefer using this server with trusted web
content or make sure your client takes precautions against prompt injections.

We appreciate feedback and suggestions from developers on how this tool can make it easier for them to build a more secure user experience, but will treat these exclusively as feature requests, and not vulnerabilities in chrome-devtools-mcp itself.

### MCP roots

`chrome-devtools-mcp` supports [MCP roots](https://modelcontextprotocol.io/specification/2025-06-18/client/roots). If the client specifies them, the MCP server will check the roots when accessing files.
Note that the MCP server always retains access to the OS-provided tmp directory. We treat security issues in the MCP roots implementation as low-severity issues because it is an optional configuration. To have full
filesystem sandboxing, we recommend using OS sandbox mechanisms.

### Network guardrails

Optional `--allowed-url-pattern` and `--blocked-url-pattern` arguments configure the **browser** to reject access to the identified URLs. Note that this is not a complete network sandbox and it only applies to Chrome DevTools targets while `chrome-devtools-mcp` is attached to them.
To have a full network sandbox, we recommend using a separate OS/VM sandbox mechanism.
To write properly, you must focus on three core pillars: correct grammar and mechanics, a clear structural flow, and simplicity in your word choice. Writing well is less about using fancy words and more about making sure your reader understands your exact message without effort.Here is a practical breakdown of how to improve your writing instantly:1. Master the Sentence BasicsStick to Subject + Verb: Every standard sentence needs a clear subject (the person or thing acting) and a verb (the action). Keep them close together so the reader doesn't get lost.Capitalize Proper Nouns: Always capitalize specific names of people, places, days of the week, months, and brands (e.g., Jane, Paris, Monday, Google). General words (e.g., woman, city, day, company) stay lowercase.Use Active Voice: Instead of writing "The ball was thrown by Leo," write "Leo threw the ball." It is shorter, punchier, and easier to read.2. Follow a Clear ProcessWriting rarely comes out perfectly on the first try. A professional approach involves distinct steps:Drafting: Write your ideas down quickly without worrying about mistakes.Editing: Go back to fix your grammar, spelling, and sentence structures.Proofreading: Read the text out loud to catch awkward phrasing or missing punctuation.3. Keep it SimpleAccording to an expert guide on writing from the University of Edinburgh, “use simple, common words instead of obscure words; use a simple, direct form of writing rather than putting on airs and graces.”Avoid overly complex vocabulary or long, winding sentences just to sound smart.
