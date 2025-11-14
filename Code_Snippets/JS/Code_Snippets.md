### Event Delegation On Whole Document

I was doing project called To Do List. I run into a problem where I create new Parent box it multiplies child elements creation. I fixed it with event delegation, which I added on the whole document. It helps with dynamically created elements too. 

This code helped me when I was creating a new container and a container within the container.

```javascript
// Event delegation for adding goals
document.addEventListener('click', function(event) {
    if (event.target.classList.contains('add-goal')) {
        const goalBox = event.target.closest('.goals-box');
        if (!goalBox) return; // If no goal box container found, exit
        addGoal(event);
    } else if (event.target.classList.contains('add')) {
        renderGoal();
    }
});
```

#### Summary
It helped me with dynamically adding elements to the page.