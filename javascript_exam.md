# JavaScript Comprehensive Exam
**Time Limit: 4 hours**  
**Total Points: 150**

## Instructions
- Complete all questions in order
- Test your code in a browser
- Comment your code properly
- Handle edge cases and errors
- You may use online documentation

---

## Section A: Core JavaScript & Functions (25 points)

### Question 1: Array & Object Manipulation (10 points)

Create a `StudentGradeManager` with the following:

**a)** Create an array of student objects with properties: `id`, `name`, `grades` (array of numbers), `dateEnrolled`. **(3 points)**

**b)** Write a function `calculateGPA(student)` that returns the average of grades rounded to 2 decimal places. **(3 points)**

**c)** Write a function `getTopStudents(students, count)` that returns the top N students by GPA. **(4 points)**

### Question 2: Date & Time Functions (15 points)

**a)** Create a function `formatDate(date, format)` that accepts a Date object and format string ("DD/MM/YYYY", "MM-DD-YYYY", "YYYY.MM.DD") and returns formatted date. **(5 points)**

**b)** Write a function `calculateAge(birthDate)` that returns age in years, months, and days as an object. **(5 points)**

**c)** Create a function `getNextBirthday(birthDate)` that returns how many days until next birthday. **(5 points)**

---

## Section B: DOM Manipulation & Events (40 points)

### Question 3: Interactive Todo List (40 points)

Create a complete todo list application with the following HTML structure and functionality:

**HTML Structure:** *(Provided - don't change)*
```html
<!DOCTYPE html>
<html>
<head>
    <title>Todo Manager</title>
    <style>
        .completed { text-decoration: line-through; color: gray; }
        .priority-high { border-left: 4px solid red; }
        .priority-medium { border-left: 4px solid orange; }
        .priority-low { border-left: 4px solid green; }
    </style>
</head>
<body>
    <div id="todoApp">
        <h1>My Todo List</h1>
        <div id="addTodoForm">
            <input type="text" id="todoInput" placeholder="Enter todo...">
            <select id="prioritySelect">
                <option value="low">Low</option>
                <option value="medium">Medium</option>
                <option value="high">High</option>
            </select>
            <button id="addBtn">Add Todo</button>
        </div>
        <div id="filters">
            <button class="filter-btn active" data-filter="all">All</button>
            <button class="filter-btn" data-filter="active">Active</button>
            <button class="filter-btn" data-filter="completed">Completed</button>
        </div>
        <ul id="todoList"></ul>
        <div id="stats">
            <span id="totalCount">0</span> total, 
            <span id="activeCount">0</span> active, 
            <span id="completedCount">0</span> completed
        </div>
    </div>
</body>
</html>
```

**JavaScript Requirements:**

**a) Todo Object Structure (5 points)**
Each todo should have: `id`, `text`, `completed`, `priority`, `createdAt`, `completedAt`

**b) Core Functions (15 points)**
- `addTodo(text, priority)` - Add new todo with unique ID and current timestamp **(5 points)**
- `toggleTodo(id)` - Toggle completion status and set completedAt **(5 points)**
- `deleteTodo(id)` - Remove todo from list **(5 points)**

**c) DOM Event Handlers (10 points)**
- Add todo on button click and Enter key press **(3 points)**
- Toggle completion on todo item click **(3 points)**
- Delete todo on delete button click **(2 points)**
- Filter todos (all/active/completed) on filter button click **(2 points)**

**d) Display & Updates (10 points)**
- `renderTodos(filter)` - Display todos based on current filter **(5 points)**
- `updateStats()` - Update count displays **(3 points)**
- Apply priority CSS classes correctly **(2 points)**

---

## Section C: AJAX & JSON (35 points)

### Question 4: Weather Dashboard (35 points)

Create a weather dashboard that fetches and displays weather data:

**HTML Structure:** *(Provided)*
```html
<!DOCTYPE html>
<html>
<head>
    <title>Weather Dashboard</title>
</head>
<body>
    <div id="weatherApp">
        <h1>Weather Dashboard</h1>
        <div>
            <input type="text" id="cityInput" placeholder="Enter city name...">
            <button id="searchBtn">Get Weather</button>
        </div>
        <div id="currentWeather" style="display:none;">
            <h2 id="cityName"></h2>
            <p>Temperature: <span id="temperature"></span>°C</p>
            <p>Description: <span id="description"></span></p>
            <p>Humidity: <span id="humidity"></span>%</p>
            <p>Last Updated: <span id="lastUpdated"></span></p>
        </div>
        <div id="forecast"></div>
        <div id="savedCities">
            <h3>Saved Cities</h3>
            <ul id="cityList"></ul>
        </div>
    </div>
</body>
</html>
```

**Requirements:**

**a) Mock Weather API (10 points)**
Since you can't access real APIs in exam, create a mock function:
```javascript
function getMockWeatherData(city) {
    // Return mock data for different cities
    // Include: temperature, description, humidity, forecast (3 days)
    // Handle invalid city names
}
```

**b) Fetch & Display Weather (10 points)**
- `fetchWeather(city)` - Get weather data and handle errors **(5 points)**
- `displayWeather(data)` - Update DOM with weather information **(5 points)**

**c) Local Storage Integration (10 points)**
- `saveCityToLocalStorage(city)` - Save searched cities **(3 points)**
- `loadSavedCities()` - Load and display saved cities on page load **(4 points)**
- `removeCityFromStorage(city)` - Remove city from saved list **(3 points)**

**d) Forecast Display (5 points)**
- Display 3-day forecast with dates and weather info **(5 points)**

---

## Section D: jQuery Implementation (25 points)

### Question 5: Image Gallery with jQuery (25 points)

Convert the following vanilla JavaScript functionality to jQuery:

**HTML Structure:** *(Provided)*
```html
<!DOCTYPE html>
<html>
<head>
    <title>Image Gallery</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        .gallery { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
        .gallery img { width: 100%; height: 200px; object-fit: cover; cursor: pointer; }
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); }
        .modal-content { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); max-width: 80%; max-height: 80%; }
        .close { position: absolute; top: 10px; right: 20px; color: white; font-size: 30px; cursor: pointer; }
    </style>
</head>
<body>
    <div id="galleryApp">
        <h1>My Photo Gallery</h1>
        <div>
            <input type="file" id="fileInput" multiple accept="image/*">
            <button id="uploadBtn">Upload Images</button>
        </div>
        <div>
            <input type="text" id="searchInput" placeholder="Search images...">
            <select id="sortSelect">
                <option value="name">Sort by Name</option>
                <option value="date">Sort by Date</option>
                <option value="size">Sort by Size</option>
            </select>
        </div>
        <div id="gallery" class="gallery"></div>
        
        <!-- Modal for full-size image -->
        <div id="imageModal" class="modal">
            <span class="close">&times;</span>
            <img class="modal-content" id="modalImage">
            <div id="imageInfo"></div>
        </div>
    </div>
</body>
</html>
```

**jQuery Requirements:**

**a) File Upload Handler (8 points)**
- Handle multiple file selection with jQuery **(3 points)**
- Read files and create image previews **(3 points)**
- Store image data (name, size, upload date) **(2 points)**

**b) Gallery Display & Events (8 points)**
- Display images in grid using jQuery **(3 points)**
- Click event to open modal with full-size image **(3 points)**
- Close modal on close button or outside click **(2 points)**

**c) Search & Sort Functionality (9 points)**
- Filter images by name using search input **(4 points)**
- Sort images by name, date, or size **(5 points)**

---

## Section E: Advanced Integration (25 points)

### Question 6: Complete Dashboard Application (25 points)

Create a personal dashboard that combines all previous concepts:

**Requirements:**

**a) Dashboard Layout (5 points)**
Create sections for: Clock, Weather, Todo Summary, Image Count, and Notes

**b) Real-time Clock (5 points)**
- Display current time updating every second
- Show both digital time and date
- Include day of the week

**c) Data Integration (10 points)**
- Load weather for default city on page load **(3 points)**
- Display todo summary (total, active, completed) **(3 points)**
- Show count of uploaded images **(2 points)**
- Quick notes section with local storage **(2 points)**

**d) Responsive Events (5 points)**
- All sections update when underlying data changes
- Smooth transitions and animations
- Error handling for all operations

---

## Bonus Section: Error Handling & Validation (10 extra points)

### Question 7: Comprehensive Error Handling

**a)** Add form validation to all input fields with custom error messages **(5 points)**

**b)** Implement try-catch blocks for all file operations and JSON parsing **(3 points)**

**c)** Create a notification system for success/error messages **(2 points)**

---

## Submission Requirements

1. **Code Organization**: Separate files for each section (HTML, CSS, JS)
2. **Comments**: Explain complex logic and function purposes
3. **Testing**: Demonstrate all features work with sample data
4. **Browser Compatibility**: Test in at least Chrome/Firefox

## Expected Skills Demonstrated:
- DOM manipulation and event handling
- Date/Time operations
- JSON parsing and localStorage
- jQuery syntax and methods
- AJAX concepts (with mock data)
- Error handling and validation
- Responsive UI updates
- File handling and reading

## Grading Criteria:
- **Functionality (60%)**: Features work as specified
- **Code Quality (20%)**: Clean, readable, well-organized code
- **Error Handling (10%)**: Proper validation and error management
- **User Experience (10%)**: Intuitive interface and smooth interactions

**Time Management Tip**: Spend 1 hour on Section A&B, 1.5 hours on Section C&D, 1 hour on Section E, and 30 minutes for testing and refinement.

**Good luck!**