<script setup>
</script>

<template>
    <section id="home" class="lg:h-[85vh] flex items-center justify-between bg-light-primary dark:bg-dark-primary py-32 lg:py-0 overflow-hidden">
        <div class="container mx-auto-h-full">
            <div class="flex flex-col md:flex-row items-center h-full pt-8">
                <div class="flex-1 flex flex-col items-center lg:items-start text-center lg:text-left">
                    <p class="text-3xl text-accent mb-[33px]">안녕하세요, I am Randalf 👋 </p>
                    <h1 class="text-4xl leading-[44px] md:text-5xl md:leading-tight lg:text-7xl lg:leading-[1.2] font-bold md:tracking-[-2px]">
                        I Build & Design <br /> Web Interfaces, Services and APIs.
                    </h1>
                    <p class="pt-4 pb-8 md:pt-6 md:pb-12 max-w-[480px] text-lg lg:text-left">
                        Explore my portfolio and see how my skills and experience can help bring your next project to life.
                    </p>
                    <button class="rounded-lg btn btn-md bg-dark-navy-500 dark:bg-dark-navy-500 text-white dark:text-white hover:bg-light-secondary hover:text-light-tail-500 md:btn-lg transition-all">
                        Work with me
                    </button>
                </div>
                <div class="flex-1 justify-end items-center h-full mt-8 md:mt-0">
                    <img class="rounded-lg" src="http://127.0.0.1:8000/img/hero.jpg" alt="Hero Image">
                </div>
            </div>
        </div>
    </section>    
</template>