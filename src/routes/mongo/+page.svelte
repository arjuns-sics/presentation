<script lang="ts">
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	let code: ReturnType<typeof Code>
</script>

<Presentation options={{ history: true, transition: 'slide', controls: true, progress: true }}>
	<!-- Introduction Slide -->
	<Slide class="h-full place-content-center place-items-center">
		<h1 class="text-8xl font-bold">Introduction</h1>
		<h1 class="text-7xl font-bold">to MongoDB</h1>
	</Slide>

	<!-- What is MongoDB? -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">What is MongoDB?</h1>
		<Transition class="mx-auto mt-8 max-w-prose">
			<p>
				MongoDB is a NoSQL database that stores data in flexible, JSON-like documents. It offers
				scalability and performance by allowing a schema-less design.
			</p>
		</Transition>
		<Transition class="mx-auto mt-8">
			<Code
				lang="json"
				code={`{
  "_id": "1234567890",
  "name": "John Doe",
  "age": 30,
  "address": {
    "street": "123 Main St",
    "city": "New York",
    "state": "NY"
  }
}`}
			/>
		</Transition>
	</Slide>

	<!-- Traditional DBs vs MongoDB -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">Traditional DBs vs MongoDB</h1>
		<Transition class="mx-auto mt-8 max-w-prose">
			<p>
				Traditional databases are SQL-based with fixed schemas, tables, rows, and columns. In
				contrast, MongoDB uses collections and documents, providing greater flexibility.
			</p>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				code={`// SQL example
function getUsers() {
  return db.query("SELECT * FROM users");
}`}
			/>
		</Transition>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				code={`// MongoDB example
function getUsers() {
  return db.collection('users').find({});
}`}
			/>
		</Transition>
	</Slide>

	<!-- CRUD Operations in MongoDB -->
	<Slide class="h-full place-content-center place-items-start px-16 text-start">
		<h1 class="text-8xl font-bold">CRUD Operations in MongoDB</h1>
		<Transition class="mx-auto mt-8 max-w-prose">
			<Code
				lang="js"
				code={`// Create
db.collection('users').insertOne({ name: "Alice", age: 25 });

// Read
db.collection('users').find({ age: { $gt: 20 } });

// Update
db.collection('users').updateOne({ name: "Alice" }, { $set: { age: 26 } });

// Delete
db.collection('users').deleteOne({ name: "Alice" });
`}
			/>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16">
		<h1 class="text-4xl font-bold">MongoDB in Real-World Scaling</h1>
		<Transition class="mx-auto mt-8 max-w-1/2">
			<p class="max-w-prose text-2xl">
				Leading companies harness MongoDB's flexible and scalable architecture to handle massive,
				real-time data.
			</p>
		</Transition>
		<Transition class="mx-auto mt-8">
			<Code
				lang="js"
				bind:this={code}
				code={`// Uber: Managing dynamic ride data
db.collection('rides').insertOne({
    rideId: 101,
    status: "active",
    location: {
        lat: 37.7749,
        lng: -122.4194
    }
});`}
			/>
		</Transition>
		<Action
			do={() => {
				code.update`// eBay: High-volume transaction logging
db.collection('transactions').insertOne({
    transactionId: 202,
    user: "buyer123",
    amount: 99.99
});`
			}}
		/>
		<Action
			do={() => {
				code.update`// Foursquare: Real-time check-in updates
db.collection('checkins').updateOne({
    userId: 303
}, {
    $set: {
        location: "San Francisco"
    }
});`
			}}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-center ">
		<h1 class=" font-bold">Conclusion</h1>
		<Transition class="px-8 ">
			<p class="mt-8 max-w-prose text-2xl">
				MongoDB offers a modern, scalable approach to data storage by providing flexible schemas and
				high performance. Its design empowers developers to build innovative solutions that
				efficiently handle vast amounts of data.
			</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center px-16 text-center">
		<h1 class="mb-16 text-6xl font-bold">What we have learnt</h1>
		<ul class="ml-8 list-disc text-2xl">
			<li>HTML and text formatting elements</li>
			<li>React components and hooks</li>
			<li>What is the fs module in Node?</li>
			<li>An intro to MongoDB</li>
		</ul>
	</Slide>
</Presentation>
