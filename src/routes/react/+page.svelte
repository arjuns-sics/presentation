<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	import { ShoppingCart } from '@lucide/svelte'
	let code: ReturnType<typeof Code>
	let componentcode: ReturnType<typeof Code>
	let result: HTMLHeadingElement
</script>

<Presentation options={{ history: true, transition: 'slide', controls: true, progress: true }}>
	<Slide class="h-full place-content-center place-items-center">
		<h1 class="text-8xl font-bold">Introduction</h1>
		<h1 class="text-7xl font-bold">to React</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">What are React Components?</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="html"
				bind:this={code}
				code={`function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}`}
			/>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code bind:this={componentcode} lang="html" code={`<App/>	`} />
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<div class="border-2 border-black p-4">
				<h2 bind:this={result} class="text-4xl font-bold">Hello World!</h2>
			</div>
		</Transition>
		<Action
			do={() => code.update`function App({ name }) {
  return (
    <div className="App">
      <h1>Hello {name}</h1>
    </div>
  );
}`}
		/>
		<Action
			do={() => {
				componentcode.update`<App name="World"/>`
			}}
		/>
		<Action
			do={() => {
				componentcode.update`<App name="World"/>
<App name="Arjun"/>`
			}}
		/>
		<Action
			do={() => {
				result.innerHTML = `Hello World! <br/> Hello Arjun!`
			}}
		/>
	</Slide>
	<!-- state -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">State</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="html"
				code={`function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}`}
			/>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<p>This is a stateless (or pure) component</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>Let's think about a practical example: <br /> a cart of items and an add to cart button.</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<div class="relative">
			<ShoppingCart size={100} />
			<div class="absolute -top-3 -right-6 rounded-full bg-red-500 px-3 py-1">
				<div>3</div>
			</div>
		</div>
		<Transition class="mx-auto mt-8 max-w-prose">
			<button class="rounded border-2 border-white bg-transparent p-4 text-2xl text-white"
				>Add to Cart</button
			>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="html"
				bind:this={code}
				code={`function App() {
					return (
						<div>
							<ShoppingCart count={3} />
							<button>Add to Cart</button>
						</div>
					)
				}`}
			/>
		</Transition>
		<Action
			do={() => {
				code.update`function App() {
			const [count, setCount] = useState(3);
			return (
				<div>
					<ShoppingCart count={count} />
					<button onClick={() => setCount(count + 1)}>Add to Cart</button>
				</div>
			)
		}`
			}}
		/>
	</Slide>
</Presentation>
