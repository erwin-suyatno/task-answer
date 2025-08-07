# Answer Task - Vue 3 Programming Exercise Application

A modern, interactive Vue 3 application built with Vite that provides programming exercises with interactive solutions and code execution capabilities.

## ✨ Features

- **⚡ Vue 3** - Latest version with Composition API
- **🚀 Vite** - Lightning fast development server and build tool
- **🎯 Vue Router** - Official router for single-page applications
- **💎 Composition API** - More flexible and powerful component logic
- **🎨 Modern UI** - Beautiful and responsive design with tab system
- **📱 Mobile Responsive** - Works perfectly on all devices
- **🔧 Interactive Code Execution** - Run and test programming solutions
- **📝 Programming Exercises** - Multiple programming challenges with solutions

## 🚀 Quick Start

### Prerequisites

Make sure you have Node.js (version 16 or higher) installed on your machine.

### Installation

1. Clone or download this project
2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:3000`

## 📖 How to Use the Application

### 🎯 Main Interface

The application features a clean, modern interface with:

- **Navigation Bar**: Contains the application title "Answer Task"
- **Tab System**: Two main tabs for different programming exercises
- **Interactive Content**: Each tab contains exercises with interactive solutions

### 📋 Available Exercises

#### Task 1 (30% Complete) - JSON Data Transformation
**Exercise**: Transform JSON data arrays into visual string representations

**What you'll learn:**
- Array manipulation and mapping
- Data transformation techniques
- String formatting and output generation

**How to use:**
1. Click on the "Task 1 30%" tab
2. Read the problem statement in the left column
3. Choose between "Solution 1" or "Solution 2" buttons
4. Click "Process Code" to see the output
5. Review the detailed explanation of the algorithm

**Sample Input:**
```javascript
[[0,2,3,4,6,8,9,11,13],
[0,3,6,8,10,11,13],
[0,2,4,6,9,10,11,13],
[0,2,3,4,6,8,10,11,13],
[0,2,3,4,6,8,9,11,13]]
```

**Expected Output:**
```
- x - - - x - x - - x - x –
- x x - x x - x - x - - x –
- x - x - x - x x - - - x –
- x - - - x - x - x - - x –
- x - - - x - x - - x - x –
```

#### Task 2 (70% Complete) - Advanced Data Transformation
**Exercise**: Transform data arrays with cell merging capabilities

**What you'll learn:**
- Advanced array manipulation
- Cell merging algorithms
- HTML table generation
- Complex data structure handling

**How to use:**
1. Click on the "Task 2 70%" tab
2. Review the problem statement and expected output image
3. Click "Solution 1" to view the solution
4. Click "Process Code" to see both console output and HTML table
5. Study the algorithm explanation

**Sample Input:**
```javascript
[[0,1,2,3],
[0,3,1,2],
[1,2,3,4],
[2,3,1,4],
[0,2,2,3]]
```

### 🔧 Interactive Features

#### Code Execution
- **Process Code Button**: Executes the solution code and displays results
- **Real-time Output**: See immediate results of code execution
- **Multiple Solutions**: Compare different approaches to the same problem

#### Solution Navigation
- **Tab Switching**: Easily switch between different exercises
- **Solution Selection**: Choose between different solution approaches
- **Detailed Explanations**: Each solution includes comprehensive algorithm explanations

#### Visual Feedback
- **Syntax Highlighting**: Code is properly formatted and highlighted
- **Responsive Layout**: Works on desktop, tablet, and mobile devices
- **Smooth Animations**: Modern UI with smooth transitions and animations

### 🎨 User Interface Elements

#### Navigation
- **Brand Link**: Click "Answer Task" to return to the main page
- **Tab Headers**: Click tab titles to switch between exercises
- **Active Tab Indicator**: Visual indication of the currently active tab

#### Content Areas
- **Left Column**: Contains the problem statement and requirements
- **Right Column**: Contains interactive solutions and code execution
- **Solution Cards**: Well-organized solution presentation with action buttons

#### Interactive Elements
- **Solution Buttons**: Toggle between different solution approaches
- **Process Buttons**: Execute code and display results
- **Code Blocks**: Syntax-highlighted code examples
- **Output Display**: Real-time code execution results

## 📁 Project Structure

```
answer/
├── public/
│   ├── output2.png      # Exercise output visualization
│   └── vite.svg         # Vite logo
├── src/
│   ├── components/      # Reusable Vue components
│   │   ├── TabSystem.vue        # Tab navigation system
│   │   ├── TabOneContent.vue    # Task 1 exercise content
│   │   ├── TabTwoContent.vue    # Task 2 exercise content
│   │   └── HelloWorld.vue       # Example component
│   ├── router/          # Vue Router configuration
│   │   └── index.js
│   ├── views/           # Page components
│   │   └── Home.vue     # Main application view
│   ├── App.vue          # Main application component
│   ├── main.js          # Application entry point
│   └── style.css        # Global styles
├── index.html           # HTML template
├── package.json         # Dependencies and scripts
├── vite.config.js       # Vite configuration
└── README.md           # This file
```

## 🛠️ Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm run lint` - Run ESLint to check code quality

## 🎯 Learning Objectives

### Programming Concepts Covered
- **Array Manipulation**: Working with nested arrays and data transformation
- **String Processing**: Converting data structures to formatted strings
- **Algorithm Design**: Creating efficient solutions for data processing
- **Code Organization**: Structuring code for readability and maintainability

### Technical Skills Developed
- **JavaScript ES6+**: Modern JavaScript features and syntax
- **Vue 3 Composition API**: Modern Vue.js development patterns
- **Interactive Development**: Real-time code execution and testing
- **Problem Solving**: Breaking down complex problems into manageable solutions

## 🎨 Customization

### Adding New Exercises
1. Create a new component in `src/components/` (e.g., `TabThreeContent.vue`)
2. Add the new tab to the tabs array in `src/views/Home.vue`:

```javascript
const tabs = [
  { title: 'Task 1 30%' },
  { title: 'Task 2 70%' },
  { title: 'Task 3 New' }  // Add new tab
]
```

3. Add the corresponding template slot:

```vue
<template #tab-2>
  <TabThreeContent />
</template>
```

### Modifying Existing Exercises
- Edit the content in the respective `TabXContent.vue` files
- Update the solution logic in the script sections
- Modify the styling in the style sections

### Adding New Features
- **New Interactive Elements**: Add buttons, forms, or other interactive components
- **Additional Code Execution**: Implement new code processing functions
- **Enhanced Visualizations**: Add charts, graphs, or other visual elements

## 🎯 Key Technologies

- **Vue 3**: Progressive JavaScript framework with Composition API
- **Vite**: Next-generation frontend tooling for fast development
- **Vue Router**: Official routing solution for single-page applications
- **ESLint**: JavaScript linting utility for code quality
- **Prettier**: Code formatter for consistent styling

## 📚 Learn More

- [Vue 3 Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Vue Router Documentation](https://router.vuejs.org/)
- [JavaScript Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

## 🤝 Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**Happy coding and learning! 🚀**

*This application is designed to help developers practice programming concepts through interactive exercises with real-time code execution capabilities.*
