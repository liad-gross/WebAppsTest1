Q1 - Reactivity
- v-model syncs the textarea to stickie.text on every keystroke
- stickie.text lives inside stickies in data(), so Vue makes it reactive
-When stickie.text changes, Vue re-renders anything that depends on it

Q2 - Deep Watch
- deep: true tells Vue to also watch inside the array, including stickie.text on each object
- without it, typing in a textarea changes stickie.text but the watcher never fires, so saveToStorage() never gets called and edits are lost when the page refreshes.

Q3 - localStorage
1. localStorage stores strings
2. we use JSON.stringify() when saving because stickies is an array of objects so JSON.stringify() converts it to a string so localStorage can hold it
3.if we forgot JSON.parse when loading, we would get the raw string back instead of an array.

Q4 - Delete logic
1. .filter() would return a new array containing only items where the condition is true
2. We assign the result back to stickies so that the stickies is now equal to the filtered result (just filtering doesnt modify the original)
3. !== means keep those who are not this id and === means keep only those who are this id and remove the rest

Q5 - Architecture Design
- Putting the logic in its own method means it can be reused anywhere and changed in one place, instead of duplicating localStorage code every time you need to save.