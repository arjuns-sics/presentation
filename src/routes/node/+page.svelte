<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	import { FileText } from '@lucide/svelte'

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
		<h1 class="text-7xl font-bold">to Node.js fs Module</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">What is the fs module?</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			The fs (File System) module allows interacting with the file system in a way modeled on
			standard POSIX functions. It is used to read from, write to, and manipulate files and
			directories in Node.js.
		</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				bind:this={code}
				code={`const fs = require('fs'); // CommonJS
/* OR */
import fs from 'fs'; // ESM`}
			/>
		</Transition>
	</Slide>
	<!-- Reading Files -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">Reading Files</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			In Node.js, you can read files using the `fs.readFile()` function, which is asynchronous.
			Here's an example:
		</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				bind:this={code_2}
				code={`const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});`}
			/>
		</Transition>
		<Action
			do={() => {
				code_2.update`const fs = require('fs');

// Read a file asynchronously
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data); // Logs the content of example.txt
});`
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			This is the basic syntax of `fs.readFile()`. It takes three arguments: the file path, the
			encoding, and a callback function that is called when the file is read.
		</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">Writing Files</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			We can write to files using the `fs.writeFile()` method. This method writes data to a file
			asynchronously.
		</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				bind:this={code_3}
				code={`const fs = require('fs');

// Write to a file asynchronously
fs.writeFile('example.txt', 'Hello, Node.js!', (err) => {
  if (err) throw err;
  console.log('File written!');
});`}
			/>
		</Transition>
		<Action
			do={() => {
				code_3.update`const fs = require('fs');

// Write to a file asynchronously
fs.writeFile('example.txt', 'Hello, Node.js!', (err) => {
  if (err) throw err;
  console.log('File written!'); // Logs when file is written
});`
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			Notice that we used `fs.writeFile()`, which writes data to the file. If the file does not
			exist, it will be created.
		</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">Asynchronous vs. Synchronous</h1>
	</Slide>
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<p>
			Node.js provides both asynchronous and synchronous methods for working with the file system.
			The asynchronous methods use callbacks, while the synchronous ones block the execution.
		</p>
		<p>For example:</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				code={`const fs = require('fs');

// Synchronous read
const data = fs.readFileSync('example.txt', 'utf8');
console.log(data);`}
			/>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				code={`const fs = require('fs');

// async read
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
console.log('File read happens asynchronously'); // logs before file is read`}
			/>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<p>
				While `fs.readFileSync()` blocks the execution until the file is read, `fs.readFile()`
				allows other tasks to run while the file is being read.
			</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-start">
		<h1 class="mb-16 text-6xl font-bold">Next topic: MongoDB</h1>
		<a href="https://arjuns-sics.github.io/presentation/mongo">
			<img
				src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/MongoDB_Logo.svg/1200px-MongoDB_Logo.svg.png"
				alt="html element"
				class="scale-75 bg-gray-300 object-contain p-12"
			/>
		</a>
	</Slide>
</Presentation>
