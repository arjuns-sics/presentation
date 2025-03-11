<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	import { ShoppingCart } from '@lucide/svelte'

	let code: ReturnType<typeof Code>
	let code_2: ReturnType<typeof Code>
	let code_3: ReturnType<typeof Code>
	let componentcode: ReturnType<typeof Code>
	let result: HTMLHeadingElement
	let count = $state(3)
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
		<Transition
			class="mx-auto mt-8 max-w-prose"
			do={code.update`function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}`}
		>
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
			<Code bind:this={componentcode} lang="jsx" code={`<App/>`} />
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
				<div>{count}</div>
			</div>
		</div>
		<Transition class="mx-auto mt-8 max-w-prose">
			<button
				onclick={() => (count += 1)}
				class="rounded border-2 border-white bg-transparent p-4 text-2xl text-white hover:cursor-pointer"
				>Add to Cart</button
			>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="html"
				bind:this={code_2}
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
				code_2.update`function App() {
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
		<Action
			do={() => {
				code_2.selectLines`2`
				code_2.update`function App() {
			const [count, setCount] = useState(3); // useState is a hook in React
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
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>Hooks are functions that let you hook into React features like state and lifecycle.</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>useEffect</p>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="jsx"
				bind:this={code_3}
				code={`import { useState, useEffect } from 'react';
import React, { useState, useEffect } from 'react';

function Example1() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component rendered or count changed:', count);
  });

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
    </div>
  );
}`}
			/>
		</Transition>
		<Action
			do={() => {
				code_3.selectLines`7-9`
			}}
		/>
		<Action
			do={() => {
				code_3.selectLines`*`
				code_3.update`import React, { useState, useEffect } from 'react';

function Example2() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Effect runs only once when component mounts');
  }, []); // Empty dependency array

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
    </div>
  );
}`
			}}
		/>
		<Action
			do={() => {
				code_3.update`import React, { useState, useEffect } from 'react';

function Example3() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('Alice');

  useEffect(() => {
    console.log('Effect runs when "count" changes:', count);
  }, [count]); // Dependency array with "count"

  useEffect(() => {
    console.log('Effect runs when "name" changes:', name);
  }, [name]); // Dependency array with "name"

  return (
    <div>
      <p>Count: {count}</p>
      <p>Name: {name}</p>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
      <button onClick={() => setName('Bob')}>Change Name</button>
    </div>
  );
}`
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-center">
		<h1 class="mb-16 text-6xl font-bold">Next topic: Node JS (FS)</h1>
		<a href="https://arjuns-sics.github.io/presentation/node">
			<img
				src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Node.js_logo.svg/2560px-Node.js_logo.svg.png"
				alt="html element"
				class="mx-auto w-1/2 rounded-lg bg-gray-300 object-contain p-4"
			/>
		</a>
	</Slide>
</Presentation>
