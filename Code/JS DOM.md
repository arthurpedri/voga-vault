script defer -> only executes after html is loaded
script async -> will execute as soon as it is able to
in the DOM, document is the parent of html
document.querySelector('css selector') : returns first element that matches the selector
document.getElementById('id')
document.getElementsByClassName('class')
document.getElementsByTagName('tag')
.style.cssProperty : setting style equal to empty string will return to the original style
.parentNode, .children : traversing 
document.createElement('tag')
parent.appendChild(child)
parent.removeChild(child)
element.hidden = true : not the same use case as display: none
element.event = function; 
.addEventListener(event, function)
.onevent = function
.removeEventListener(event, function) : an event listener with an anonynous function cannot be removed
events : click, wheel, mouseover, keypress, keydown... (element events on mdn)

