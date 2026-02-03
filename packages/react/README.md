# `@marksmith/react`

A React server component to render markdown content.

## Installation

```bash
npm install @marksmith/react
```

> [!NOTE]  
> This package is **not available on npm yet**. There is already another package with a similar name, `mark-smith`, which prevents publishing as `marksmith`. I'm currently brainstorming another name.


## Usage

```tsx
import { Markdown } from "@marksmith/react";

export function Article({ content }: { content: string }) {
	return (
		<div className="prose">
			<Markdown content={content} />
		</div>
	);
}
```

It is possible to customize how markdown nodes are rendered by through the `components` property. In this example, we're modifying the rendering logic of code blocks and links.


```tsx
import { Markdown } from "@marksmith/react";

export function Article({ content }: { content: string }) {
	return (
		<div className="prose">
			<Markdown
				content={content}
				components={{
					CodeBlock: ({ content, info }) => {
						// Highlight the content using a syntax highlighting library, etc.
						return (
							<pre data-lang={info}>
								<code>{content}</code>
							</pre>
						);
					},
					Link: ({ href, children }) => {
						// Validate the link destination, etc.
						return (
							<a href={href} rel="noreferrer">
								{children}
							</a>
						);
					},
				}}
			/>
		</div>
	);
}
```