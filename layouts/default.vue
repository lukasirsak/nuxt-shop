<template>
    <header>
        <nav class="bg-gray-800">
            <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
                <div class="relative flex h-16 items-center justify-between">
                    <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
                        <div class="flex flex-shrink-0 items-center">
                            <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company">
                        </div>
                        <div class="hidden sm:ml-6 sm:block">
                            <div class="flex space-x-4">
                                <NavLink to="/">Dashboard</NavLink>
                                <NavLink to="/products">Products</NavLink>
                                <NavLink to="/contact">Contact</NavLink>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>

    </header>

    <main>
        <slot/>
    </main>

    <footer>
        <!-- TODO -->
    </footer>
</template>

<script setup>
    // 
</script>