<script>
    import { onMount } from 'svelte';
    import { faBars } from "@fortawesome/free-solid-svg-icons";

    import { faHtml5, faCss3Alt, faReact, faVuejs, faNodeJs, faJava, faJsSquare, faGithub, faTwitter, faLinkedin } from "@fortawesome/free-brands-svg-icons";

    import { FontAwesomeIcon } from "@fortawesome/svelte-fontawesome";

    let menuOpen = false;
    function toggleMenu() {
        menuOpen = !menuOpen;
    }

    const skills= [
        {icon: faHtml5, color:"text-orange-600"},
        {icon: faCss3Alt, color:"text-red-600"},
        {icon: faJsSquare, color:"text-red-500"},
        {icon: faReact, color:"text-green-500"},
        {icon: faVuejs, color:"text-purple-500"},
        {icon: faNodeJs, color:"text-pink-400"},
        {icon: faJava, color:"text-gray-600"},
        {icon: faGithub, color:"text-blue-600"}
    ];

    const projects = [
        {title: "Project 1", description: "Description 1", photo: "https://via,placeholder.com/150", link:"#"},
        {title: "Project 2", description: "Description 2", photo: "https://via,placeholder.com/150", link:"#"},
        {title: "Project 3", description: "Description 3", photo: "https://via,placeholder.com/150", link:"#"},
        {tittle: "Password Generator", description: "A Password generator", photo: "/ImageGenerator.png/", link:"https://manuelmmedina.github.io/password-generator.github.io/"},
    ]

    function handleSubmit(event) {
        event.preventDefault();
        const name = document.getElementById("name").value;
        const email = document.getElementById("email").value;
        const message = document.getElementById("message").value;

        alert(`Datos del formulario recibidos:\nNombre: ${name}\nEmail: ${email}\nMessage: ${message}`);
    }

</script>

<header class="bg-white bg-opacity-90 shadow-lg top-0 left-0 w-full z-50">
    <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
        <div class="text-2xl hover:text-white">
            <span>&lt;CLB /&gt;</span>
        </div>
        <div class="hover:text-indigo-500 test-2xl">
            <div class="hidden md:flex space-x-4 items-center">
                <a href="about-me" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">About Me</a>
                <a href="skills" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Skills</a>
                <a href="projects" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Projects</a>
                <a href="contact" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Contact</a>
            </div>
        </div>
        <div class="md:hidden">
            <button on:click={toggleMenu} aria-label="Open Menu" class="text-indigo hover:text-indigo-700 focus:outline-none">
                <FontAwesomeIcon icon={faBars} class="text-2xl"/>
            </button>
        </div>
    </nav>

    { #if menuOpen}
        <div class="absolute bg-white shadow-md w-full md:hidden">
            <ul class="flex flex-col p-4">
                <li>
                    <a href="about-me" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">About Me</a>
                </li>
                <li>
                    <a href="skills" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Skills</a>
                </li>
                <li>
                    <a href="projects" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Projects</a>
                </li>
                <li>
                    <a href="contact" class="text-indigo-500 hover:text-indigo-700 px-3 py-2 text-sm font-medium">Contact</a>
                </li>
            </ul>
        </div>
    {/if}
</header>

<!--About me -->

<section id="about-me" class="py-20 flex flex-col lg:flex-row items-center bg-gradient-to-br from-teal-400 via-blue-600 to-indigo-700 text-white w-full">
    <div class="flex justify-center lg:w-1/3 lg:mb-0">
        <img src="/peru.jpg/" alt="viva peru" class="bg-white rounded-full w-48 h-48 shadow-2xl ring-4 ring-indigo-700 hover:ring-cyan-300 transition-all duration-300 transform hover:-translate-y-2 hover:scale-105"/>
    </div>
    <div>
        <h1 class="text-5xl font-extrabold leading-tight mb-4">About me</h1>
        <p class="text-lg mt-2 text-gray-300 mb-4">Hi, my name is Manuel</p>
    </div>
</section>

<!-- Skills -->

<section id="skills" class="py-20 flex flex-col lg:flex-row items-center bg-gradient-to-br from-teal-400 via-blue-300 to-indigo-700 text-white w-full">
    <div class="container mx-auto px-6">
        <h2 class="text-2xl font-bold text-indigo-700 text-center">Skills</h2>
        <div class="grid grid-cols-3 md:grid-cols-4 gap-6 place-items-center">
            {#each skills as skills}
                <div class="group relative p-6 w-1/2 md:w-1/4 lg:w-1/6">
                    <FontAwesomeIcon icon={skills.icon} class="{skills.color} text-5xl transition-transform hover:scale-110"></FontAwesomeIcon>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Projects -->

<section id="projects" class="py-20 bg-gradient-to-br from-teal-400 via-blue-600 to-indigo-700 text-white w-full">
    <div class='container mx-auto px-6'>
        <h2 class="text-2xl font-bold text-center">Projects</h2>
        <div class="flex flex-wrap justify-center gap-4 mt-6">
            {#each projects as project}
                <div class="p-6 md:w-1/3 w-1/2 lg:w-1/4 bg-white border-gray-300 rounded-lg shadow-md text-center">
                    <img src="{project.photo}" alt={project.title} class="w-full h-32 object-cover rounded-b-md nb-4"/>
                    <h3 class="text-xl font-semibold text-indigo-700 mb-2"> {project.title}</h3>
                    <p class="text-sm text-gray-700 mb-4"> {project.description}</p>
                    <a href={project.link} target="_blank" class="text-indigo-500 hover:text-indigo-700">See project</a>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Contact form-->

<section id="contact-form" class="oy-12 bg-white">
    <div class="container mx-auto px-6 max-w-lg">
        <h2 class="text-2xl font-bold text-indigo-700 text-center mb-6">Contact</h2>
        <form class="bg-gray-100 shadow-md rounded px-8 pt-6 pb-8 mb-4" on:submit={handleSubmit}>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="name">Name</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline"
                       id="name" type="text" placeholder="Type your name">
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="email">Email</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline"
                       id="email" type="email" placeholder="Type your email">
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2" for="message">Message</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline"
                       id="message" type="text" placeholder="Type your message">
            </div>
            <div class="flex items-center justify-center">
                <button class="bg-indigo-700 text-white hover:bg-indigo-700 font-bold p-4 rounded focus:outline-none focus:shadow-outline" type="submit">Send</button>
            </div>
        </form>
    </div>
</section>
