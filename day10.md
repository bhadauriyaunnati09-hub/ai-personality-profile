Day 10: Personal Portfolio Website
<title>Unnati Bhadauriya | Portfolio</title>
<meta name="description" content="Portfolio of Unnati Bhadauriya - Python Enthusiast and Aspiring Developer">
<script src="https://cdn.tailwindcss.com"></script>
<style>
html{
scroll-behavior:smooth;
}
.typing{
overflow:hidden;
white-space:nowrap;
border-right:3px solid #14b8a6;
animation:typing 4s steps(40,end) infinite alternate;
}
@keyframes typing{
from{width:0}
to{width:100%}
}
</style>
</head>

<body class="bg-gray-950 text-white">

<!-- Navbar -->
<nav class="fixed w-full bg-gray-900 shadow-lg z-50">
<div class="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
<h1 class="text-xl font-bold text-teal-400">Unnati</h1>

<div class="space-x-5 hidden md:block">
<a href="#about" class="hover:text-teal-400">About</a>
<a href="#skills" class="hover:text-teal-400">Skills</a>
<a href="#projects" class="hover:text-teal-400">Projects</a>
<a href="#contact" class="hover:text-teal-400">Contact</a>
</div>

<button onclick="toggleTheme()" class="bg-teal-500 px-3 py-1 rounded">
🌙
</button>
</div>
</nav>

<!-- Hero -->
<section class="min-h-screen flex items-center justify-center text-center px-6">
<div>
<h1 class="text-5xl md:text-7xl font-bold mb-4">
Unnati Bhadauriya
</h1>

<div class="typing text-xl md:text-2xl text-teal-400 mx-auto max-w-lg">
Python Enthusiast | Aspiring Developer
</div>

<p class="mt-6 text-gray-300 max-w-2xl mx-auto">
Passionate Python enthusiast and aspiring developer from Bhind,
Madhya Pradesh. I enjoy learning programming, building projects,
and exploring new technologies.
</p>

<div class="mt-8 flex justify-center gap-4">
<a href="mailto:bhadauriyaunnati09@gmail.com"
class="bg-teal-500 px-5 py-3 rounded-lg hover:bg-teal-600">
Email
</a>

<a href="https://github.com/bhadauriyaunnati09-hub/ai-personality-profile"
target="_blank"
class="border border-teal-500 px-5 py-3 rounded-lg hover:bg-teal-500">
GitHub
</a>
</div>
</div>
</section>

<!-- About -->
<section id="about" class="py-20 px-6">
<div class="max-w-5xl mx-auto">
<h2 class="text-4xl font-bold text-center mb-10 text-teal-400">
About Me
</h2>

<p class="text-lg text-gray-300 leading-8 text-center">
I am Unnati Bhadauriya, a passionate Python learner and aspiring
developer. My goal is to continuously improve my programming skills,
build meaningful projects, and create innovative software solutions.
</p>
</div>
</section>

<!-- Skills -->
<section id="skills" class="py-20 bg-gray-900">
<div class="max-w-5xl mx-auto px-6">
<h2 class="text-4xl font-bold text-center mb-12 text-teal-400">
Skills
</h2>

<div class="grid md:grid-cols-3 gap-8">

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="font-bold text-xl mb-4">Technical</h3>
<span class="bg-teal-500 px-3 py-2 rounded">Python</span>
</div>

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="font-bold text-xl mb-4">Tools</h3>
<span class="bg-purple-500 px-3 py-2 rounded">VS Code</span>
<span class="bg-purple-500 px-3 py-2 rounded">GitHub</span>
</div>

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="font-bold text-xl mb-4">Soft Skills</h3>
<span class="bg-pink-500 px-3 py-2 rounded">Communication</span>
<span class="bg-pink-500 px-3 py-2 rounded">Problem Solving</span>
<span class="bg-pink-500 px-3 py-2 rounded">Teamwork</span>
</div>

</div>
</div>
</section>

<!-- Projects -->
<section id="projects" class="py-20 px-6">
<div class="max-w-6xl mx-auto">
<h2 class="text-4xl font-bold text-center mb-12 text-teal-400">
Projects
</h2>

<div class="grid md:grid-cols-3 gap-8">

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="text-xl font-bold mb-3">AI Personality Profile</h3>
<p class="text-gray-300">
Web-based project that creates and displays AI-generated
personality insights.
</p>
<p class="mt-3 text-teal-400">
HTML • CSS • JavaScript
</p>
</div>

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="text-xl font-bold mb-3">Personal Portfolio Website</h3>
<p class="text-gray-300">
Responsive portfolio website showcasing skills and projects.
</p>
<p class="mt-3 text-teal-400">
HTML • Tailwind CSS • JavaScript
</p>
</div>

<div class="bg-gray-800 p-6 rounded-xl">
<h3 class="text-xl font-bold mb-3">Python Calculator</h3>
<p class="text-gray-300">
Calculator application for basic arithmetic operations.
</p>
<p class="mt-3 text-teal-400">
Python
</p>
</div>

</div>
</div>
</section>

<!-- Achievements -->
<section class="py-20 bg-gray-900">
<div class="max-w-5xl mx-auto px-6">
<h2 class="text-4xl font-bold text-center mb-12 text-teal-400">
Achievements
</h2>

<ul class="space-y-4 text-lg text-gray-300">
<li>✔ Completed multiple beginner-level Python projects</li>
<li>✔ Actively learning web development and programming</li>
<li>✔ Participating in coding challenges and project-based learning</li>
</ul>
</div>
</section>

<!-- Contact -->
<section id="contact" class="py-20 px-6">
<div class="max-w-4xl mx-auto text-center">
<h2 class="text-4xl font-bold mb-10 text-teal-400">
Contact Me
</h2>

<p class="mb-4">
📍 Bhind, Madhya Pradesh, India
</p>

<p class="mb-4">
📧 bhadauriyaunnati09@gmail.com
</p>

<a href="https://www.linkedin.com/posts/unnati-bhadauriya"
target="_blank"
class="text-teal-400 underline">
LinkedIn Profile
</a>

<br><br>

<a href="https://github.com/bhadauriyaunnati09-hub/ai-personality-profile"
target="_blank"
class="text-teal-400 underline">
GitHub Repository
</a>
</div>
</section>

<footer class="bg-gray-950 text-center py-6 border-t border-gray-800">
<p>© 2026 Unnati Bhadauriya | Portfolio Website</p>
</footer>

<script>
function toggleTheme(){
document.body.classList.toggle("bg-white");
document.body.classList.toggle("text-black");
}
</script>

</body>
</html>