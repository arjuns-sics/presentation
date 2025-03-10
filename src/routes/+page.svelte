<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	let htmltext: HTMLHeadingElement
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
			<p bind:this={htmltext} class="mt-8 text-4xl">
				You can put other elements inside an element.
			</p>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code bind:this={code} lang="html" code={`<p>My cat is <strong>very</strong> grumpy.</p>`} />
		</Transition>
		<Action
			do={() => {
				code.update`<p>My cat is <strong>very grumpy.</p></strong>`
				htmltext.innerHTML =
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
</Presentation>
