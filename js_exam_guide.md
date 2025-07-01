# Comprehensive JavaScript Exam Guide

## 01 - Defining the Role of JavaScript in Development

### JavaScript vs Compiled Languages
- **JavaScript**: Interpreted language, executed at runtime by the browser's JavaScript engine
- **Compiled Languages**: Code is transformed into machine code before execution
- JavaScript can be used for:
  - Frontend development (browser)
  - Backend development (Node.js)
  - Mobile apps (React Native)
  - Desktop apps (Electron)

### Client-Server Architecture
- **Client**: Browser that requests and displays web pages
- **Server**: Computer that hosts and serves web content
- **JavaScript roles**:
  - Client-side: User interface, form validation, DOM manipulation
  - Server-side: API handling, database operations, server logic

### Development Ecosystem
- **Package Managers**: npm, yarn
- **Build Tools**: Webpack, Vite, Parcel
- **Frameworks**: React, Vue, Angular
- **Testing**: Jest, Mocha, Cypress
- **Version Control**: Git, GitHub

## 02 - JavaScript Fundamentals

### Syntax and Basic Concepts

#### Variables and Data Types
```javascript
// Variable declarations
let name = "John";          // String
const age = 25;             // Number
var isActive = true;        // Boolean
let data = null;            // Null
let undefined_var;          // Undefined

// Arrays
let fruits = ["apple", "banana", "orange"];

// Objects
let person = {
    name: "Alice",
    age: 30,
    city: "Paris"
};
```

#### Control Structures
```javascript
// If-else
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}

// Switch
switch (day) {
    case "Monday":
        console.log("Start of week");
        break;
    case "Friday":
        console.log("TGIF!");
        break;
    default:
        console.log("Regular day");
}

// Loops
for (let i = 0; i < 5; i++) {
    console.log(i);
}

while (condition) {
    // code
}

for (let fruit of fruits) {
    console.log(fruit);
}

for (let key in person) {
    console.log(key + ": " + person[key]);
}
```

### Functions
```javascript
// Function declaration
function greet(name) {
    return "Hello, " + name;
}

// Function expression
const multiply = function(a, b) {
    return a * b;
};

// Arrow function
const add = (a, b) => a + b;

// Function with default parameters
function introduce(name = "Anonymous", age = 0) {
    return `I'm ${name}, ${age} years old`;
}
```

### Object Manipulation
```javascript
// Creating objects
const car = {
    brand: "Toyota",
    model: "Camry",
    year: 2022,
    start: function() {
        console.log("Engine started");
    }
};

// Accessing properties
console.log(car.brand);        // Dot notation
console.log(car["model"]);     // Bracket notation

// Adding properties
car.color = "blue";

// Deleting properties
delete car.year;

// Object methods
Object.keys(car);              // Returns array of keys
Object.values(car);            // Returns array of values
Object.entries(car);           // Returns array of [key, value] pairs
```

## 03 - DOM Manipulation

### Understanding the DOM
The DOM (Document Object Model) is a programming interface that represents HTML documents as a tree structure.

### DOM Tree Structure
```
Document
├── html
    ├── head
    │   ├── title
    │   └── meta
    └── body
        ├── h1
        ├── div
        │   ├── p
        │   └── span
        └── footer
```

### Selecting Elements
```javascript
// By ID
const element = document.getElementById("myId");

// By class name
const elements = document.getElementsByClassName("myClass");

// By tag name
const paragraphs = document.getElementsByTagName("p");

// Query selectors (CSS-style)
const firstDiv = document.querySelector("div");
const allDivs = document.querySelectorAll("div");
const specificElement = document.querySelector("#myId .myClass");
```

### Manipulating Elements
```javascript
// Change content
element.innerHTML = "<strong>New HTML content</strong>";
element.textContent = "New text content";

// Change attributes
element.setAttribute("class", "newClass");
element.getAttribute("id");
element.removeAttribute("style");

// Change styles
element.style.color = "red";
element.style.backgroundColor = "yellow";
element.style.display = "none";

// Add/remove CSS classes
element.classList.add("newClass");
element.classList.remove("oldClass");
element.classList.toggle("activeClass");
element.classList.contains("someClass");
```

### Creating and Removing Elements
```javascript
// Create elements
const newDiv = document.createElement("div");
const newText = document.createTextNode("Hello World");

// Add content
newDiv.appendChild(newText);
newDiv.innerHTML = "<p>Paragraph content</p>";

// Insert into DOM
document.body.appendChild(newDiv);
parentElement.insertBefore(newDiv, existingChild);

// Remove elements
parentElement.removeChild(childElement);
element.remove(); // Modern way
```

## 04 - Event Management

### Understanding Events
Events are actions that happen in the browser (clicks, key presses, page loads, etc.)

### Event Handling Methods
```javascript
// Method 1: HTML attribute (not recommended)
<button onclick="handleClick()">Click me</button>

// Method 2: DOM property
button.onclick = function() {
    console.log("Button clicked!");
};

// Method 3: addEventListener (recommended)
button.addEventListener("click", function() {
    console.log("Button clicked!");
});

// Arrow function version
button.addEventListener("click", () => {
    console.log("Button clicked!");
});
```

### Common Events
```javascript
// Mouse events
element.addEventListener("click", handleClick);
element.addEventListener("dblclick", handleDoubleClick);
element.addEventListener("mouseenter", handleMouseEnter);
element.addEventListener("mouseleave", handleMouseLeave);

// Keyboard events
document.addEventListener("keydown", handleKeyDown);
document.addEventListener("keyup", handleKeyUp);

// Form events
form.addEventListener("submit", handleSubmit);
input.addEventListener("change", handleChange);
input.addEventListener("input", handleInput);

// Window events
window.addEventListener("load", handlePageLoad);
window.addEventListener("resize", handleResize);
```

### Event Object
```javascript
function handleEvent(event) {
    console.log(event.type);           // Event type
    console.log(event.target);         // Element that triggered event
    console.log(event.currentTarget);  // Element with event listener
    
    // Prevent default behavior
    event.preventDefault();
    
    // Stop event bubbling
    event.stopPropagation();
}
```

### Form Handling
```javascript
// Form validation
function validateForm(event) {
    event.preventDefault(); // Prevent form submission
    
    const name = document.getElementById("name").value;
    const email = document.getElementById("email").value;
    
    if (name.trim() === "") {
        alert("Name is required");
        return false;
    }
    
    if (!isValidEmail(email)) {
        alert("Please enter a valid email");
        return false;
    }
    
    // Submit form if validation passes
    event.target.submit();
}

function isValidEmail(email) {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(email);
}
```

## 05 - jQuery

### Introduction to jQuery
jQuery is a JavaScript library that simplifies DOM manipulation, event handling, and AJAX.

### jQuery Syntax
```javascript
// Basic syntax: $(selector).action()
$(document).ready(function() {
    // Code executes when DOM is ready
});

// Shorter version
$(function() {
    // Code here
});
```

### Selectors
```javascript
// Basic selectors
$("#myId")           // ID selector
$(".myClass")        // Class selector
$("p")              // Element selector
$("*")              // All elements

// Attribute selectors
$("[href]")          // Elements with href attribute
$("[href='#']")      // Elements with href="#"

// Pseudo selectors
$("p:first")         // First paragraph
$("tr:even")         // Even table rows
$("input:visible")   // Visible input elements
```

### DOM Manipulation with jQuery
```javascript
// Get/Set content
$("#myDiv").html();                    // Get HTML content
$("#myDiv").html("<p>New content</p>"); // Set HTML content
$("#myDiv").text("New text");          // Set text content

// Get/Set attributes
$("#myImg").attr("src");               // Get attribute
$("#myImg").attr("src", "new.jpg");    // Set attribute
$("#myInput").val();                   // Get input value
$("#myInput").val("new value");        // Set input value

// CSS manipulation
$("#myDiv").css("color", "red");       // Set single CSS property
$("#myDiv").css({                      // Set multiple properties
    "color": "red",
    "font-size": "16px"
});

// Add/Remove classes
$("#myDiv").addClass("newClass");
$("#myDiv").removeClass("oldClass");
$("#myDiv").toggleClass("activeClass");
```

### Event Handling with jQuery
```javascript
// Click event
$("button").click(function() {
    alert("Button clicked!");
});

// Multiple events
$("input").on("focus blur", function() {
    $(this).toggleClass("highlight");
});

// Event delegation (for dynamic content)
$(document).on("click", ".dynamic-button", function() {
    console.log("Dynamic button clicked");
});

// Custom events
$("div").trigger("customEvent");
$("div").on("customEvent", function() {
    console.log("Custom event triggered");
});
```

### AJAX with jQuery
```javascript
// GET request
$.get("api/data.json", function(data) {
    console.log(data);
});

// POST request
$.post("api/save", {name: "John", age: 30}, function(response) {
    console.log("Data saved:", response);
});

// AJAX with more options
$.ajax({
    url: "api/users",
    method: "GET",
    dataType: "json",
    success: function(data) {
        console.log("Success:", data);
    },
    error: function(xhr, status, error) {
        console.log("Error:", error);
    }
});
```

## Regular Expressions (Regex)

### Basic Regex Patterns
```javascript
// Create regex
const pattern1 = /hello/;              // Literal notation
const pattern2 = new RegExp("hello");  // Constructor

// Basic matching
const text = "Hello world";
console.log(pattern1.test(text));      // false (case sensitive)
console.log(/hello/i.test(text));      // true (case insensitive)
```

### Common Regex Patterns
```javascript
// Email validation
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

// Phone number (simple)
const phoneRegex = /^\d{3}-\d{3}-\d{4}$/;

// Password (at least 8 chars, 1 uppercase, 1 lowercase, 1 number)
const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d@$!%*?&]{8,}$/;

// URL validation
const urlRegex = /^https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)$/;
```

### Regex Methods
```javascript
const text = "The year is 2023";
const yearRegex = /\d{4}/g;

// test() - returns boolean
console.log(yearRegex.test(text));     // true

// exec() - returns match details
console.log(yearRegex.exec(text));     // ["2023", index: 12, input: "The year is 2023"]

// String methods with regex
text.match(/\d+/g);                    // ["2023"]
text.replace(/\d{4}/, "2024");         // "The year is 2024"
text.split(/\s+/);                     // ["The", "year", "is", "2023"]
```

## Advanced JavaScript Concepts

### Promises and Async/Await
```javascript
// Promise
const fetchData = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data received");
        }, 1000);
    });
};

// Using promises
fetchData()
    .then(data => console.log(data))
    .catch(error => console.error(error));

// Async/await
async function getData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

### Local Storage
```javascript
// Store data
localStorage.setItem("username", "john_doe");
localStorage.setItem("preferences", JSON.stringify({theme: "dark"}));

// Retrieve data
const username = localStorage.getItem("username");
const preferences = JSON.parse(localStorage.getItem("preferences"));

// Remove data
localStorage.removeItem("username");
localStorage.clear(); // Remove all
```

### Error Handling
```javascript
try {
    // Code that might throw an error
    const result = riskyOperation();
    console.log(result);
} catch (error) {
    console.error("An error occurred:", error.message);
} finally {
    console.log("This always executes");
}

// Custom errors
function validateAge(age) {
    if (age < 0) {
        throw new Error("Age cannot be negative");
    }
    if (age > 150) {
        throw new Error("Age seems unrealistic");
    }
    return true;
}
```

## Exam Tips and Common Patterns

### Form Validation Example
```javascript
function validateForm() {
    const name = $("#name").val().trim();
    const email = $("#email").val().trim();
    const phone = $("#phone").val().trim();
    
    // Clear previous errors
    $(".error").remove();
    
    let isValid = true;
    
    // Name validation
    if (name === "") {
        $("#name").after('<span class="error">Name is required</span>');
        isValid = false;
    }
    
    // Email validation
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
        $("#email").after('<span class="error">Valid email is required</span>');
        isValid = false;
    }
    
    // Phone validation
    const phoneRegex = /^\d{3}-\d{3}-\d{4}$/;
    if (!phoneRegex.test(phone)) {
        $("#phone").after('<span class="error">Phone format: XXX-XXX-XXXX</span>');
        isValid = false;
    }
    
    return isValid;
}
```

### Dynamic Content Creation
```javascript
function addListItem(text) {
    const li = document.createElement("li");
    li.textContent = text;
    
    // Add delete button
    const deleteBtn = document.createElement("button");
    deleteBtn.textContent = "Delete";
    deleteBtn.onclick = function() {
        li.remove();
    };
    
    li.appendChild(deleteBtn);
    document.getElementById("myList").appendChild(li);
}

// jQuery version
function addListItemJQuery(text) {
    const li = $('<li>').text(text);
    const deleteBtn = $('<button>').text('Delete').click(function() {
        li.remove();
    });
    
    li.append(deleteBtn);
    $('#myList').append(li);
}
```

### AJAX Data Loading
```javascript
// Load and display data
function loadUsers() {
    $.ajax({
        url: 'api/users.json',
        method: 'GET',
        dataType: 'json',
        success: function(users) {
            const userList = $('#userList');
            userList.empty();
            
            users.forEach(user => {
                const userDiv = $('<div>').addClass('user');
                userDiv.html(`
                    <h3>${user.name}</h3>
                    <p>Email: ${user.email}</p>
                    <p>Phone: ${user.phone}</p>
                `);
                userList.append(userDiv);
            });
        },
        error: function() {
            alert('Failed to load users');
        }
    });
}
```

## Key Points to Remember for Exam

1. **DOM Manipulation**: Know how to select, modify, create, and delete elements
2. **Event Handling**: Understand event listeners, event objects, and form handling
3. **jQuery**: Syntax differences from vanilla JavaScript, common methods
4. **Regex**: Basic patterns for validation (email, phone, etc.)
5. **Functions**: Different ways to declare and use functions
6. **Objects and Arrays**: How to create, access, and manipulate them
7. **Error Handling**: Try-catch blocks and validation
8. **AJAX**: Making HTTP requests and handling responses
9. **Client-Server Architecture**: Understanding the role of JavaScript in web development

Practice combining these concepts in real scenarios, as exam questions often test multiple skills together!