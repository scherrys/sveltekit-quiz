<script>
	let quizName = '';
	let toggleQuizName = false;
	let nr = 0;
	let question = '';
	let answer = '';
    let quiz = { name: "", questions: []}

    const handleName = () => {
        toggleQuizName = !toggleQuizName
        quiz.name = quizName
    }

	const handleSubmit = () => {
	 	quiz.questions.push({ question, answer, id: nr })
        console.log("quiz => ", quiz)

        question = ""
        answer = ""
	};

</script>

{#if !toggleQuizName}
	<div class="flex flex-col text-sm mb-2">
		<label class="font-bold mb-2 text-gray-800" for="todo">Quiz name</label>
		<input
			type="text"
			name="quizName"
			placeholder="Name the quiz?"
			class="apperance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
			bind:value={quizName}
		/>
	</div>
	<button
		class="w-full shadow-sm bg-blue-500 rounded hover:bg-blue-600 text-white py-2 px-4"
		on:click={handleName}>Add</button
	>
{:else}
	<h4>Quiz name: {quiz.name}</h4>

    <h5>{quiz.questions}</h5>
	{#each quiz['questions'] as quest}
        <h5 class="italic">{quest.answer}</h5>
    {/each}

	<form class="my-6" on:submit|preventDefault={handleSubmit}>
		<div class="flex flex-col text-sm mb-2">
			<label class="font-bold mb-2 text-gray-800" for="todo">question nr. {nr + 1}</label>
			<input
				type="text"
				name="question"
				placeholder="quiz question?"
				class="apperance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
				bind:value={question}
			/>
			<input
				type="text"
				name="answer"
				placeholder="quiz answer?"
				class="apperance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg my-2"
				bind:value={answer}
			/>
		</div>
		<button
			class="w-full shadow-sm bg-blue-500 rounded hover:bg-blue-600 text-white py-2 px-4"
			type="submit">Add</button
		>
	</form>
{/if}
