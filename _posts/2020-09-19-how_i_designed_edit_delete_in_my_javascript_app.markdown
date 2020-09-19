---
layout: post
title:      "How I Designed Edit + Delete in My JavaScript APP"
date:       2020-09-19 13:54:37 +0000
permalink:  how_i_designed_edit_delete_in_my_javascript_app
---


When creating an Edit and a Delete functionality for a JavaScript app, I understand why one could create these as separate processes and call it a day. However, I designed my app a little differently and found I can put these together as part of the same click event listener.

The only reason I find this acceptable is because I completely understand what’s happening in my app and feel like it makes the most sense to do it this way. What’s happening is this:

In order to edit a Material, the `#material-container` needs to be clicked. I added the delete button with the Edit Resource button, but it appears only after the edit form is rendered, AFTER the `#material-container` is clicked. This means I could not add the delete button as its own clickable event without first adding it as part of the edit button’s click event.

In other words, the delete button is only visible when the edit form is visible, and I cannot have the delete button without first rendering the edit form.

This took a while for me to understand but I completely get why this was the case.

As for the delete button functionality by itself, this is the code I came up with:

```
const deleteContainer = document.getElementById("delete-button")
deleteContainer.addEventListener('click', e => {
		deleteMaterial(id)
})
```

Here, I am assigning the `#delete-button` HTML element to a variable, then adding the click event listener to that variable. The most important part here is, while inside the click event, I then added a function that accepts an argument of the material’s ID, which directs to the Fetch request so a Material can actually be deleted from the backend, shown here:

```
function deleteMaterial(id) {
    fetch(`${materialIndex}/${id}`, {
        method: "DELETE"
    })
}
```

Finally, as part of the `renderPatchForm()` in my material.js file, I added my delete button here and had to link it to each instance of Material, which is something I was missing when I first went to implement this feature:

`<input id="delete-button" **data-id="${this.id}"** type="submit" name="delete" value="Delete" class="submit">`


My edit functionality was designed a little different. A Material can be updated by clicking on any part of the Material, because the `renderMaterialCard()` function I created renders itself inside the `#material-container`. So, that entire container is click-able.

`const materialContainer = document.querySelector('#material-container')`

I assigned the `#material-container` div to a variable, and then added a click listener event to that variable. Inside that listener, I parsed the Material's ID and then assigned the Material’s ID to a variable, selected a different DIV to grab and then using `.innerHTML`, add the `renderPatchForm()` (the edit form) with that specific material information to the screen.

```
materialContainer.addEventListener('click', e => {
        const id = parseInt(e.target.closest('[data-id]').dataset.id)
        const material = Material.findById(id)
        document.querySelector('#edit-material').innerHTML = material.renderPatchForm()
```

After the delete button, the material is console.logged to the screen (for my own sanity), and then finally I select the #edit-material DIV again and add a submit event listener to submit the Edit form.

```
console.log(material)
document.querySelector('#edit-material').addEventListener('submit', e => updateForm(e))
```


This process allows me to successfully edit and delete each Material with no issues and no errors.

