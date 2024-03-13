<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    laravelVersion: String,
    phpVersion: String,
});
</script>

<template>

    <Head title="Bem-vindo" />

    <div
        class="relative sm:flex sm:justify-center sm:items-center min-h-screen bg-dots-darker bg-center bg-gray-100 dark:bg-dots-lighter dark:bg-gray-900 selection:bg-red-500 selection:text-white">
        <div class="max-w-7xl mx-auto p-6 lg:p-8">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 lg:gap-8">
                <div
                    class="scale-100 p-6 bg-white dark:bg-gray-800/50 dark:bg-gradient-to-bl from-gray-700/50 via-transparent dark:ring-1 dark:ring-inset dark:ring-white/5 rounded-lg shadow-2xl shadow-gray-500/20 dark:shadow-none flex motion-safe:hover:scale-[1.01] transition-all duration-250 focus:outline focus:outline-2 focus:outline-red-500">
                    <div>
                        <div
                            class="h-16 w-16 bg-red-30 dark:bg-red-800/20 flex items-center justify-center rounded-full">
                            <svg height="40px" width="40px" version="1.1" id="Layer_1"
                                xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                                viewBox="0 0 512 512" xml:space="preserve">
                                <polygon points="154.64,420.096 154.64,59.496 0,134 0,512 " />
                                <polygon style="fill:#333333;"
                                    points="309.288,146.464 309.288,504.472 154.64,420.096 154.64,59.496 " />
                                <polygon points="463.928,50.152 309.288,146.464 309.288,504.472 463.928,415.68 " />
                                <path style="fill:#E21B1B;" d="M414.512,281.656l-11.92-15.744c-8.8-11.472-85.6-113.984-85.6-165.048
	C317.032,39.592,355.272,0,414.512,0S512,39.592,512,100.864c0,50.992-76.8,153.504-85.488,165.048L414.512,281.656z" />
                                <circle style="fill:#FFFFFF;" cx="414.512" cy="101.536" r="31.568" />
                            </svg>
                        </div>

                        <h2 class="mt-6 text-xl font-semibold text-gray-900 dark:text-white">Mapa</h2>

                        <p class="mt-4 text-gray-500 dark:text-gray-400 text-sm leading-relaxed">
                            Veja o mapa aqui.
                        </p>
                    </div>
                    <Link href="/mapa">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
                    </svg>
                    </Link>
                </div>

                <div
                    class="scale-100 p-6 bg-white dark:bg-gray-800/50 dark:bg-gradient-to-bl from-gray-700/50 via-transparent dark:ring-1 dark:ring-inset dark:ring-white/5 rounded-lg shadow-2xl shadow-gray-500/20 dark:shadow-none flex motion-safe:hover:scale-[1.01] transition-all duration-250 focus:outline focus:outline-2 focus:outline-red-500">
                    <div>
                        <div
                            class="h-16 w-16 bg-red-30 dark:bg-red-800/20 flex items-center justify-center rounded-full">
                            <svg  height="40px" width="40px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg"
                                xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve">
                                <path style="fill:#6B6B6B;"
                                    d="M0,355.2v-324c0.104-5.704,4.696-10.296,10.4-10.4h491.2c5.704,0.104,10.296,4.696,10.4,10.4v324H0z" />
                                <path
                                    d="M512,355.2v41.6c-0.104,5.704-4.696,10.296-10.4,10.4H10.4c-5.704-0.104-10.296-4.696-10.4-10.4v-41.6H512z" />
                                <rect x="146.4" y="480.8" style="fill:#333333;" width="219.2" height="10.4" />
                                <polygon style="fill:#6B6B6B;"
                                    points="328.8,480.8 183.2,480.8 193.6,407.2 318.4,407.2 " />
                                <rect x="20.8" y="41.6" width="470.4" height="292.8" />
                                <polygon style="fill:#333333;"
                                    points="318.4,407.2 193.6,407.2 187.792,448.28 320.272,420.424 " />
                                <rect x="108.992" y="164.072" style="fill:#E21B1B;" width="18.688" height="51.104" />
                                <g>
                                    <rect x="77.856" y="184.96" style="fill:#999999;" width="18.688" height="30.208" />
                                    <rect x="140.136" y="135.672" style="fill:#999999;" width="18.688"
                                        height="79.504" />
                                </g>
                                <rect x="171.28" y="84.568" style="fill:#E21B1B;" width="18.688" height="130.608" />
                                <rect x="202.416" y="110.92" style="fill:#999999;" width="18.688" height="104.24" />
                                <g>
                                    <rect x="233.6" y="152.88" style="fill:#E21B1B;" width="18.688" height="62.464" />
                                    <path style="fill:#E21B1B;" d="M356.984,86.464c-38.328,0.008-69.392,31.088-69.384,69.416s31.088,69.392,69.416,69.384
		c38.304-0.008,69.36-31.048,69.384-69.352h-69.416V86.464z" />
                                </g>
                                <path style="fill:#FFFFFF;"
                                    d="M417.904,94.992L368.8,144.088h69.4V144C438.208,125.616,430.904,107.984,417.904,94.992z" />
                                <path style="fill:#DBDBDB;"
                                    d="M368.8,74.648v69.456l49.096-49.096C404.896,81.952,387.224,74.616,368.8,74.648z" />
                                <g>
                                    <rect x="99" y="254.984" style="fill:#999999;" width="314" height="8" />
                                    <rect x="156.128" y="294.888" style="fill:#999999;" width="199.744" height="8" />
                                </g>
                            </svg>
                        </div>

                        <h2 class="mt-6 text-xl font-semibold text-gray-900 dark:text-white">Gráfico</h2>

                        <p class="mt-4 text-gray-500 dark:text-gray-400 text-sm leading-relaxed">
                            Veja o gráfico aqui.
                        </p>
                    </div>
                    <Link href="/grafico">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
                    </svg>
                    </Link>
                </div>
            </div>
        </div>
    </div>
</template>

<style>
.bg-dots-darker {
    background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(0,0,0,0.07)'/%3E%3C/svg%3E");
}

@media (prefers-color-scheme: dark) {
    .dark\:bg-dots-lighter {
        background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(255,255,255,0.07)'/%3E%3C/svg%3E");
    }
}
</style>
