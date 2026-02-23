# Reflection
## Q1 - Reactivity
### When you type inside the `<textarea>`, the character counter updates automatically.
### **Explain why this happens.**
### Your answer must mention: v-model, Vue reactivity, and what data property changes.

The textarea has the v-model attribute that ties it to stickie.text for the given note being rendered. Because it's tied to the stickie.text attribute using v-model, stickie.text will automatically update whenever the value of the textarea is changed. Vue reactivity makes sure that the stickie.text attribute is automatically updated when input is put in the textarea. The character counter always renders the result of the charCount method, which is derived directly from stickies.text, so the character counter updates automatically when the textarea value, and therefore stickies.text, changes.

## Q2 - Deep Watch
### We use a deep watcher.
### Explain what deep: true does and what would stop working if we removed it.

deep: true makes it so that the watcher handler will run when any inner property of the object is changed. If we removed it, the watcher would only run when the whole object was replaced with a completely new value.

## Q3 - localStorage
### 1. What type of data does localStorage store?

It stores text/string data.

### 2. Why do we use `JSON.stringify()` when saving?

Because localStorage stores string data, we must convert our JSON object to a string to be saved properly.

### 3. What would happen if we forgot `JSON.parse()` when loading?

If we forgot JSON.parse() when loading, the stickies would be loaded in as a string rather than an actual object, and we wouldn't be able to succesfully render the stickies.

## Q4 - Delete logic
### What does `.filter()` return?

.filter() will return a new list only containing items that match the condition passed in.

### Why assign the result back to this.stickies?

It returns a new list, so we must assign it back to this.stickies to update the page.

### Why `!== and not ===?

Using !== keeps all the other elements, but removes the one element matching the id that we're removing.

## Q5 - Architecture decision
### Why is saving implemented in a separate method ( `saveToStorage` ) instead of writing localStorage code directly in the watcher?

Saving is implemented in a separate method abstracs the localStorage saving logic into its own spot, keeping the watcher clean and just there for watching the changes and calling the method when necessary. If we ever need to change saving logic, it can just be done in the method and the watcher will automatically handle it correctly.