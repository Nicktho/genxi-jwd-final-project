# Task 9: Persisting Tasks to LocalStorage

## Description

In this task, we'll _persist_ (ie: save) our tasks to LocalStorage, so that we can load them again the next time we visit our page.

## Walkthrough

### Step 1: Adding the save method to TaskManager

> #### Useful Resources for this step
> - [Using the Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
> - [JSON.stringify()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)

In this step, we'll add a `save()` method to our TaskManager, that we can call to save the current `this.tasks` to localStorage.

Because `localStorage` can only store strings, we need a way to convert our `this.tasks` array to a string, that can also be converted _back_ to an array when we load the tasks. For this, we'll be using [JSON.stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify), which we can [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) later on to convert back to an array.

1. In `js/taskManager.js`, in the `TaskManager` class, create a `save` method. This method doesn't require any parameters.
2. In the `save` method, create a JSON string of the tasks using `JSON.stringify()` and store it to a new variable, `tasksJson`.
3. Store the JSON string in `localStorage` under the key `tasks` using `localStorage.setItem()`
4. In `js/index.js`, after both adding a new task and updating a task's status to done, call `taskManager.save()` to save the tasks to `localSorage`.

> #### Test Your Code!
> Now is a good chance to test your code, follow the steps below:
> 1. Open `index.html` in the browser and create a new task using the form.
> 2. Open the developer tools and navigate to the `Application` tab.
> 3. In the sidebar, under `Storage`, expand `Local Storage` and select `file://`
>
> **Expected Result**
> You should see a key `tasks` with the stringified array of tasks as it's value.
> ![Image of Expected Result](images/1.png)

### Step 2: Adding the load method to TaskManager

> #### Useful Resources for this step
> - [Using the Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
> - [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

Now that we have saved our tasks to `localStorage`, we need a way to load them back into our `TaskManager` when we load the application.

For this, we'll be transforming the array we _stringified_ with `JSON.stringify()` back to an array, using `JSON.parse()`, before storing them back into the `TaskManager`'s `this.tasks`.

1. In `js/taskManager.js`, add a new method called `load`. This method doesn't require any parameters.
2. In the `load` method, get the JSON string of tasks stored in `localStorage` with `localStorage.getItem()`, making sure to pass the key we used to save the tasks, `tasks`. Store this string into a new variable, `tasksJson`.
3. Convert the `tasksJson` string to an array using `JSON.parse()` and store it in `this.tasks`.\
4. In `js/index.js`, near the top of the file, after _instantiating_ `taskManager`, `load` the tasks with `taskManager.load()` and render them with `taskManager.render()`.

## Results

Open up `index.html` and add a task. Now, when you re-visit the page (eg: close and open or refresh), you should see the previously created task loaded and rendered to the page! 

## Example

Stuck? Check out the provided example in the [example/](example/) folder
