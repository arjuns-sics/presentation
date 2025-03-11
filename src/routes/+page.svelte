<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	let htmltext: HTMLHeadingElement
	let htmltext_2: HTMLHeadingElement
	let code: ReturnType<typeof Code>
	let htmlstructure: ReturnType<typeof Code>
</script>

<Presentation options={{ history: true, transition: 'slide', controls: true, progress: true }}>
	<Slide class="h-full place-content-center place-items-center">
		<!-- intro to html -->
		<h1 class="text-8xl font-bold">Introduction</h1>
		<h1 class="text-7xl font-bold">to HTML</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<!-- html what is html? -->
		<Transition>
			<h1 bind:this={htmltext} class="text-8xl font-bold">What is HTML?</h1>
		</Transition>
		<Transition do={() => htmltext.classList.replace('text-8xl', 'mb-16')}>
			<p class="max-w-prose text-4xl">
				<span>Hyper</span><span>Text</span> <span>Markup</span> <span>Language</span>
			</p>
		</Transition>
		<Transition>
			<p class="mt-8 max-w-prose text-3xl">
				<b>HyperText</b> <br />refers to links that connect web pages to one another, either within
				a single website or between websites.
			</p>
		</Transition>
		<Transition>
			<p class="mt-8 max-w-prose text-3xl">
				<b>Markup Language</b><br /> A text-encoding system which specifies the structure and formatting
				of a document
			</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<!-- html what is html? -->
		<h1 class="text-8xl font-bold">HTML Elements</h1>
		<Transition>
			<p class="mt-8 max-w-prose text-3xl">
				An element consists of a opening tag, content, and a closing tag.
			</p>
			<img
				src="https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Basic_HTML_syntax/grumpy-cat-small.png"
				alt="html element"
				class="mt-8"
			/>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<Transition>
			<p bind:this={htmltext_2} class="mt-8 text-4xl">
				You can put other elements inside an element.
			</p>
		</Transition>
		<Transition
			class="mx-auto mt-8 max-w-prose"
			do={() => code.update`<p>My cat is <strong>very grumpy.</strong></p>`}
		>
			<Code bind:this={code} lang="html" code={`<p>My cat is <strong>very</strong> grumpy.</p>`} />
		</Transition>
		<Action
			do={() => {
				code.update`<p>My cat is <strong>very grumpy.</p></strong>`
				htmltext_2.innerHTML =
					"You can't put elements in the wrong order. ❌ <br/> Last opened element should be closed first."
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<!-- structure of an html page -->
		<Transition class="h-full">
			<Code
				lang="html"
				bind:this={htmlstructure}
				code={`<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>`}
			/>
		</Transition>
		<Action
			do={() => {
				htmlstructure.selectLines`1`
			}}
		/>
		<Action
			do={() => {
				htmlstructure.selectLines`2,10`
			}}
		/>
		<Action
			do={() => {
				htmlstructure.selectLines`3,6`
			}}
		/>
		<Action
			do={() => {
				htmlstructure.selectLines`7,9`
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<img
			src="https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Basic_HTML_syntax/template-screenshot.png"
			alt=""
			class="scale-150 object-contain"
		/>
	</Slide>
	<!-- text formatting elements -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<Transition>
			<p
				class="max-w -prose
			mt-8 text-3xl"
			>
				HTML provides a number of elements that help you to structure text in a document.
			</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<div class="flex flex-col">
			<Transition class="flex items-center justify-between gap-5">
				<Code lang="html" code={`<h1>Heading level 1</h1>`} />
				<h1 class="w-full">Heading level 1</h1>
			</Transition>
			<Transition class="flex items-center gap-5">
				<Code lang="html" code={`<h2>Heading level 2</h2>`} />
				<h2 class="w-full">Heading level 2</h2>
			</Transition>
			<Transition class="flex items-center gap-5">
				<Code lang="html" code={`<h3>Heading level 3</h3>`} />
				<h3 class="w-full">Heading level 3</h3>
			</Transition>
			<Transition class="flex items-center gap-5">
				<Code lang="html" code={`<h4>Heading level 4</h4>`} />
				<h4 class="w-full">Heading level 4</h4>
			</Transition>
			<Transition class="flex items-center gap-5">
				<Code lang="html" code={`<h5>Heading level 5</h5>`} />
				<h5 class="w-full">Heading level 5</h5>
			</Transition>
			<Transition class="flex items-center gap-5">
				<Code lang="html" code={`<h6>Heading level 6</h6>`} />
				<h6 class="w-full">Heading level 6</h6>
			</Transition>
		</div>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<div class="flex flex-col">
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<p>Paragraph</p>`} />
				<p class="w-full text-4xl">Paragraph</p>
			</Transition>
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<strong>Strong</strong>`} />
				<strong class="w-full">Strong</strong>
			</Transition>
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<em>Emphasis</em>`} />
				<em class="w-full">Emphasis</em>
			</Transition>
			<Transition class="flex items-center gap-16 text-end">
				<Code lang="html" code={`<mark>Marked</mark>`} />
				<mark>Marked</mark>
			</Transition>
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<del>Deleted</del>`} />
				<del class="w-full">Deleted</del>
			</Transition>
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<ins>Inserted</ins>`} />
				<ins class="w-full">Inserted</ins>
			</Transition>
			<Transition class="flex items-center gap-5 text-end ">
				<Code lang="html" code={`<p>log<sub>e</sub></p>`} />
				<p class="w-full text-4xl">log<sub>e</sub></p>
			</Transition>
			<Transition class="flex items-center gap-5 text-end">
				<Code lang="html" code={`<p>10<sup>5</sup></p>`} />
				<p class="w-full text-4xl">10<sup>5</sup></p>
			</Transition>
		</div>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<h1 class="mb-16 text-6xl font-bold">Next topic: React</h1>
		<a href="https://arjuns-sics.github.io/presentation/react">
			<img
				src="https://cdn.iconscout.com/icon/free/png-256/free-react-logo-icon-download-in-svg-png-gif-file-formats--company-brand-world-logos-vol-4-pack-icons-282599.png?f=webp&w=256"
				alt="html element"
				class="scale-125 object-contain"
			/>
		</a>
	</Slide>
</Presentation>
