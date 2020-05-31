<script>
    import { onMount } from 'svelte';
    import {fly, fade} from 'svelte/transition';

    import BurgerButton from '../components/BurgerButton.svelte';
    import DropDownMenu from '../components/DropDownMenu.svelte';

    let heroSectionVisible = false;
    let heroSectionHeight;
    let scrollValue = 0;

    let dropDownVisible = false;

    onMount(() => {
        heroSectionVisible = true;
    });

    function showMenu(){
        dropDownVisible = !dropDownVisible;
    }

    function onClick(e){
    }
</script>
<svelte:window  bind:scrollY={scrollValue}/>
<main class="text-gray-600" on:click={onClick}>
    <!-- Hero section  -->
    <div class="flex justify-start bg-1 mobile-width md:h-screen dark-text px-8" bind:clientHeight={heroSectionHeight}>
        <!-- left side -->
        <div class="flex flex-col w-4/5">
        {#if scrollValue < heroSectionHeight/2}
            <div class="flex justify-between items-start mb-10" transition:fade>
                <h1 in:fly="{{x: 80, duration: 600 }}" out:fly="{{x: -80, duration: 600 }}" class="w-full text-4xl">Portfolio</h1>
            </div>
            <h1 in:fly="{{x: -80, duration: 600 }}" out:fly="{{x: 80, duration: 600 }}" class="text-2xl sm:text-4xl my-40">Hi, I’m 
                <span class="font-semibold">Yanis</span> 
                <br/> and I help people transform their ideas into <br/> 
                <span class="font-semibold">websites</span> and 
                <span class="font-semibold">apps</span>.
            </h1>
        {/if}
        </div>

        <!-- right side -->
        <div class="flex justify-start flex-col items-end w-1/5">
            <BurgerButton class="" onClick={showMenu}/>
            {#if dropDownVisible}
            <div in:fly="{{y: -80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}">
                <DropDownMenu/>
            </div>
            {/if}
        </div>

    </div>

    <!-- Skills section -->
	<div class="flex flex-col justify-center skills-section section bg-2 light-text pb-10 mobile-width lg:h-screen">
        {#if scrollValue > heroSectionHeight/2 && scrollValue < heroSectionHeight*1.5}
        <h1 in:fly="{{x: 80, duration: 600 }}" out:fly="{{x: -80, duration: 600 }}" class="w-full text-center text-4xl mb-10">My Skills</h1>

        <div class="flex flex-col lg:flex-row self-center">
            
            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-col justify-between rounded-lg shadow-lg lg:w-1/3 text-center my-3 mx-5 bg-1 dark-text max-w-sm">

                <div>
                    <h1 class="text-2xl text-center mb-5">Web Development</h1>

                    <p class="text-lg">Android application development, including everything from the design to the deployment.</p>
                </div>
                <div>
                    <p class="text-xl">Front-End</p>
                    <div class="flex flex-row justify-center my-2">
                        <object type="image/svg+xml" data="ressources/html-5.svg" class="logo"></object>
                        <object type="image/svg+xml" data="ressources/css-3.svg" class="logo mx-1"></object>
                        <object type="image/svg+xml" data="ressources/javascript.svg" class="logo mx-1"></object>
                        <object type="image/svg+xml" data="ressources/bootstrap-4.svg" class="logo mx-1"></object>
                        <object type="image/svg+xml" data="ressources/svelte.svg" class="logo mx-1"></object>
                        <object type="image/svg+xml" data="ressources/bulma.svg" class="logo mx-1"></object>
                        <object type="image/svg+xml" data="ressources/tailwind.svg" class="logo mx-1"></object>
                    </div>

                    <p class="text-xl my-2">Back-End</p>
                    <div class="flex flex-row justify-center my-2">
                        <object type="image/svg+xml" data="ressources/django.svg" class="logo"></object>
                        <object type="image/svg+xml" data="ressources/python-5.svg" class="logo"></object>
                    </div>
                
                </div>
            </div>

            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-col justify-between rounded-lg shadow-lg lg:w-1/3 text-center px-1 my-3 mx-5 bg-1 dark-text max-w-sm">
                
                <div>
                    <h1 class="text-2xl text-center mb-5">Mobile Development</h1>

                    <p class="text-lg">Complete website development including backend using these technologies</p>
                </div>

                <div>
                    <p class="text-xl">App With</p>
                    <div class="flex flex-row justify-center my-2">
                        <object type="image/svg+xml" data="ressources/flutter.svg" class="logo"></object>
                        <object type="image/svg+xml" data="ressources/nativescript.svg" class="logo mx-1"></object>
                    </div>

                    <p class="text-xl my-2">Back-End</p>
                    <div class="flex flex-row justify-center my-2">
                        <object type="image/svg+xml" data="ressources/django.svg" class="logo"></object>
                        <object type="image/svg+xml" data="ressources/python-5.svg" class="logo"></object>
                    </div>
                
                </div>
            </div>
            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="python-card flex flex-col justify-between rounded-lg shadow-lg lg:w-1/3 text-center px-1 my-3 mx-5 bg-1 dark-text max-w-sm">
                
                <div>
                    <h1 class="text-2xl text-center mb-5">Python Scripting</h1>

                    <p class="text-lg">All the tasks that require python scripts like scraping, task automation...</p>
                </div>

                <div>
                    <p class="text-xl">With</p>
                    <div class="flex flex-row justify-center my-2">
                        <object type="image/svg+xml" data="ressources/python-5.svg" class="logo"></object>
                    </div>
                    <p class="text-xl">And</p>
                    <p class="text-md text-center my-2">All the tons of availible python packages.</p>
                
                </div>
            </div>
        </div>
        {/if}
	</div>

    <!-- Projects section -->
	<div class="flex flex-col justify-center projects-section section dark-text pb-10 bg-1 mobile-width lg:h-screen">
        {#if scrollValue > heroSectionHeight*1.5 && scrollValue < heroSectionHeight*2.5}
        <h1 in:fly="{{x: -80, duration: 600 }}" out:fly="{{x: 80, duration: 600 }}" class="w-full text-center text-4xl mb-10">My Projects</h1>

        <div class="flex flex-col lg:flex-row self-center">
            
            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-col justify-between rounded-lg shadow-xl lg:w-1/3 text-center px-2 my-3 mx-5 max-w-sm bg-2 light-text h-64">

                <div>
                    <h1 class="text-2xl text-center mb-5">Ultimate Watchlist</h1>

                    <p class="text-lg">A mobile app made using <br/> nativescript (svelte-native) with tmdb api integration.</p>
                </div>
                <div class="">
                    <!-- <p class="text-lg my-2 text-left">App: <a class="text-gray-600 underline" href="" target="blank">Google Play Store</a></p>
                    <p class="text-lg my-2 text-left">Code: <a class="text-gray-600 underline" href="" target="blank">Github Repo</a></p>
                     -->
                    <p class="text-lg my-2 text-left">App: (Link coming soon)</p>
                    <p class="text-lg my-2 text-left">Code: (Link coming soon)</p>

                </div>
            </div>

            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-col justify-between rounded-lg shadow-xl lg:w-1/3 text-center px-2 my-3 mx-5 max-w-sm bg-2 light-text h-64">

                <div>
                    <h1 class="text-2xl text-center mb-5">Github User Data</h1>

                    <p class="text-lg">Website fetching all public repos of any user from Github and export the data to pdf files.</p>
                </div>
                <div class="">
                    <p class="text-lg my-2 text-left">App: <a class="text-gray-600 underline" href="https://gh-user-data.herokuapp.com/" target="blank">Website</a></p>
                    <p class="text-lg my-2 text-left">Code: <a class="text-gray-600 underline" href="https://github.com/Karm0s/GitHub-User-Data" target="blank">Github Repo</a></p>

                </div>
            </div>

            <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-col justify-between rounded-lg shadow-xl lg:w-1/3 text-center px-2 my-3 mx-5 max-w-sm bg-2 light-text h-64">

                <div>
                    <h1 class="text-2xl text-center mb-5">GraphQL Server</h1>

                    <p class="text-lg">GraphQL API serving data about japanese animation shows parsed from an opensource json database.</p>
                </div>
                

                <div class="">
                    <p class="text-lg my-2 text-left">Code: <a class="text-gray-600 underline" href="https://github.com/Karm0s/Backend" target="blank">Github Repo</a></p>

                </div>
            </div>
        </div>
        {/if}
	</div>
	
    <!-- About Me section -->
	<div class="flex flex-col justify-center items-center about-section section bg-2 h-screen light-text bg-1">
        {#if scrollValue > heroSectionHeight*2.5 && scrollValue < heroSectionHeight*3.5}
        <h1 in:fly="{{x: 80, duration: 600 }}" out:fly="{{x: -80, duration: 600 }}" class="w-full text-center text-4xl mb-10">About Me</h1>

        <p in:fly="{{x: -80, duration: 600 }}" out:fly="{{x: 80, duration: 600 }}" class="w-full lg:w-1/2 text-xl mb-10">I am a self-taught developer. I started programming six years ago with the goal of making a game but things have changed quite a bit and now I am a university student and a freelancer.
            I am a fan of minimalism, and I always try to create minimal, clean and good looking software.</p>
        {/if}
    </div>

    <!-- Contact section -->
	<div class="flex flex-col justify-center contact-section section bg-1 h-screen dark-text">
        {#if scrollValue > heroSectionHeight*3.5}
        <h1 in:fly="{{x: -80, duration: 600 }}" out:fly="{{x: 80, duration: 600 }}" class="w-full text-center text-4xl mb-10">Contact Me</h1>

        <div in:fly="{{y: 80, duration: 600 }}" out:fly="{{y: -80, duration: 600 }}" class="flex flex-row justify-center">
            <a href="mailto:bouchenna.yanis@protonmail.com">
                <div class="btn flex justify-center items-center bg-2 w-32 h-10 rounded-lg light-text mx-5">
                    <div class="text-xl">E-Mail</div>
                </div>
            </a>

            <a href="https://twitter.com/karm0s">
                <div class="btn flex justify-center items-center bg-2 w-32 h-10 rounded-lg light-text mx-5">
                    <div class="text-xl">Twitter</div>
                </div>
            </a>
        </div>
        {/if}
	</div>

    <!-- Footer -->
	<div class="flex flex-col justify-center items-center footer-section section bg-2 light-text">
        <small>Hosted on Github</small>
        <small>&copy; Copyright {new Date().getFullYear()}, Yanis Bouchenna</small>
    </div>

	<!-- <div class="lg:container mx-auto text-center">
		<div class="w-auto">
			<h1 class="text-white bg-black w-auto">Portfolio</h1>
		</div>
		<p class="text-white bg-black text-center">Hi, I’m Yanis and I help people transform their ideas into websites and apps.</p>
	</div> -->
</main>

<style>
    .section{
        @apply px-8;
    }
    .logo{
        width: 32px;
        height: 32px;
    }
    .btn:hover{
        background-color: var(--blue);
    }
    .mobile-width{
        min-height: 100vh;
    }
</style>