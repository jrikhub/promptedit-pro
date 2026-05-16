<script setup lang="ts">
    import { ref } from 'vue'
    import { Head } from '@inertiajs/vue3'

    // Pricing toggle state
    const isAnnual = ref(true)

    // Interactive state to simulate the UI features right on the sales page
    const activeTab = ref('ai-video')

    // Alert Modal state management
    const isAlertOpen = ref(false)
    const alertMessage = ref('')
    const alertTitle = ref('')

    const openAlertModal = (title: string, message: string) => {
        alertTitle.value = title
        alertMessage.value = message
        isAlertOpen.value = true
    }

    const closeAlertModal = () => {
        isAlertOpen.value = false
    }

    const aiFeatures = {
        'ai-video': {
            title: 'Text-to-Video Engine (Powered by Veo)',
            badge: 'Veo Integration',
            prompt: 'Cinematic drone shot of a neon-lit cyberpunk city marketplace, rainy night, 8k resolution, highly detailed.',
            status: 'Generation complete (4.2s)',
            icon: '📽️'
        },
        'ai-image': {
            title: 'Rapid Asset Generation (Powered by Nano Banana)',
            badge: 'Nano Banana v2',
            prompt: 'Flat vector asset illustration of a vintage video editing cassette tape, isolated on neon purple background.',
            status: 'Generation complete (0.8s)',
            icon: '🖼️'
        }
    }

    // Rich mockup asset card items to give the layout weight
    const mockAssets = [
        { id: '01', duration: '0:12', tag: 'Cinematic' },
        { id: '02', duration: '0:08', tag: 'Cyberpunk' },
        { id: '03', duration: '0:15', tag: 'B-Roll' },
        { id: '04', duration: '0:05', tag: 'Overlay' },
    ]
</script>

<template>
    <Head title="PromptEdit Pro - Unlock Next-Gen Video Assets & AI Tools" />

    <div class="min-h-screen bg-neutral-950 text-neutral-100 font-sans selection:bg-purple-500 selection:text-white antialiased">

        <!-- Navigation Bar -->
        <nav class="sticky top-0 z-50 border-b border-neutral-900 bg-neutral-950/80 backdrop-blur-md">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
                <div class="flex items-center gap-2">
                    <span class="text-xl font-black tracking-tighter bg-gradient-to-r from-white via-neutral-200 to-neutral-400 bg-clip-text text-transparent">
                        PROMPTEDIT<span class="text-purple-500"> PRO</span>
                    </span>
                </div>
                <div class="hidden sm:flex items-center gap-6">
                    <a href="#features" class="text-sm font-medium text-neutral-400 hover:text-white transition">Features</a>
                    <a href="#preview" class="text-sm font-medium text-neutral-400 hover:text-white transition">AI Studio Preview</a>
                    <a href="#pricing" class="text-sm font-medium text-neutral-400 hover:text-white transition">Pricing</a>
                </div>
                <div>
                    <button @click="openAlertModal('Get Started', 'The registration flow is currently restricted to audition reviewers. Please use the pricing tier action buttons below to evaluate client workflows.')" class="inline-flex items-center justify-center px-5 py-2.5 text-sm font-bold rounded-full bg-white text-black hover:bg-neutral-200 transition-all duration-200 shadow-lg shadow-white/5">
                        Get Started
                    </button>
                </div>
            </div>
        </nav>

        <!-- Hero Section -->
        <header class="relative overflow-hidden pt-20 pb-16 sm:pt-28 sm:pb-24 lg:pt-36 lg:pb-32">
            <!-- Glow effect backing -->
            <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full max-w-7xl h-[500px] bg-[radial-gradient(circle_at_top,_var(--tw-gradient-stops))] from-purple-600/15 via-transparent to-transparent -z-10 pointer-events-none" />

            <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-purple-500/30 bg-purple-500/10 text-xs font-semibold text-purple-400 mb-6">
                    ✨ Welcome to the Future of Content Creation
                </div>

                <h1 class="text-4xl sm:text-6xl lg:text-7xl font-extrabold tracking-tight bg-gradient-to-b from-white to-neutral-400 bg-clip-text text-transparent mb-6 max-w-4xl mx-auto leading-tight sm:leading-none">
                    Design & build amazing video layouts, instantly.
                </h1>

                <p class="text-lg sm:text-xl text-neutral-400 max-w-2xl mx-auto mb-10 leading-relaxed">
                    Stop struggling with empty timelines. Access unlimited high-end assets, native panel extensions, and groundbreaking video generation models in one seamless workflow.
                </p>

                <div class="flex flex-col sm:flex-row items-center justify-center gap-4 max-w-md mx-auto">
                    <a href="#pricing" class="w-full sm:w-auto inline-flex items-center justify-center px-8 py-4 text-base font-bold rounded-full bg-purple-600 text-white hover:bg-purple-500 transition-all duration-200 shadow-xl shadow-purple-600/20">
                        Join the Marketplace
                    </a>
                    <a href="#preview" class="w-full sm:w-auto inline-flex items-center justify-center px-8 py-4 text-base font-semibold rounded-full bg-neutral-900 border border-neutral-800 text-neutral-300 hover:bg-neutral-800 transition">
                        See How it Works
                    </a>
                </div>
            </div>
        </header>

        <!-- Interactive UI Preview Block -->
        <section id="preview" class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-12 scroll-mt-20">
            <div class="text-center mb-8">
                <span class="text-xs font-bold text-purple-400 uppercase tracking-widest block mb-2">Interactive Preview</span>
                <h2 class="text-2xl sm:text-4xl font-bold tracking-tight text-white">An interface built for production speed</h2>
            </div>

            <div class="rounded-2xl border border-neutral-800 bg-neutral-900/40 p-3 backdrop-blur-sm shadow-2xl">
                <!-- Mock Browser/App Header -->
                <div class="rounded-xl border border-neutral-800 bg-neutral-950 overflow-hidden flex flex-col min-h-[480px]">

                    <!-- Tab Selectors -->
                    <div class="border-b border-neutral-900 bg-neutral-900/30 p-3 flex flex-col sm:flex-row sm:items-center justify-between gap-3 text-xs">
                        <div class="flex items-center gap-2 overflow-x-auto pb-1 sm:pb-0">
                            <button @click="activeTab = 'ai-video'" :class="[activeTab === 'ai-video' ? 'bg-neutral-800 text-white border-neutral-700' : 'text-neutral-500 border-transparent']" class="px-3 py-1.5 rounded-lg border font-medium transition whitespace-nowrap">
                                🎬 AI Video Generator (Veo)
                            </button>
                            <button @click="activeTab = 'ai-image'" :class="[activeTab === 'ai-image' ? 'bg-neutral-800 text-white border-neutral-700' : 'text-neutral-500 border-transparent']" class="px-3 py-1.5 rounded-lg border font-medium transition whitespace-nowrap">
                                🎨 Rapid Asset Creator (Nano Banana)
                            </button>
                        </div>
                        <div class="flex items-center gap-2 text-neutral-400 font-mono text-[11px] bg-neutral-950 px-3 py-1.5 rounded border border-neutral-900 self-start sm:self-auto">
                            <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse" />
                            API Connection Stable
                        </div>
                    </div>

                    <!-- Sandbox UI Simulation Area -->
                    <div class="flex-1 grid grid-cols-1 lg:grid-cols-5 divide-y lg:divide-y-0 lg:divide-x divide-neutral-900">
                        <!-- Sidebar Controls -->
                        <div class="lg:col-span-2 p-6 flex flex-col justify-between bg-neutral-900/10">
                            <div>
                                <span class="text-[10px] uppercase font-bold tracking-wider text-purple-400 px-2 py-0.5 rounded bg-purple-950/50 border border-purple-900/50">
                                    {{ aiFeatures[activeTab].badge }}
                                </span>
                                <h3 class="text-base font-bold text-white mt-3 mb-4">
                                    {{ aiFeatures[activeTab].title }}
                                </h3>

                                <label class="block text-xs font-semibold text-neutral-400 mb-2">Generation Prompt</label>
                                <div class="w-full bg-neutral-950 border border-neutral-800 rounded-xl p-3 font-mono text-xs text-neutral-300 leading-relaxed min-h-[80px]">
                                    {{ aiFeatures[activeTab].prompt }}
                                </div>
                            </div>

                            <div class="mt-6 pt-6 border-t border-neutral-900/60">
                                <div class="flex justify-between items-center text-xs mb-3 text-neutral-500">
                                    <span>Output: 16:9 Aspect Ratio</span>
                                    <span>{{ aiFeatures[activeTab].status }}</span>
                                </div>
                                <button @click="openAlertModal('Model Variation', 'Running a live variation requires active API quota keys. This sandbox layout showcases production layout compliance without consuming credits.')" class="w-full bg-purple-600 hover:bg-purple-500 text-white text-xs font-bold py-3 px-4 rounded-xl transition shadow-lg shadow-purple-600/10 flex items-center justify-center gap-2">
                                    ⚡ Generate Variation
                                </button>
                            </div>
                        </div>

                        <!-- Asset Grid Output Showcase Area -->
                        <div class="lg:col-span-3 p-6 bg-neutral-950 flex flex-col justify-center">
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                                <div v-for="asset in mockAssets" :key="asset.id" class="border border-neutral-800 rounded-xl bg-neutral-900/30 p-2 relative group overflow-hidden aspect-video flex flex-col justify-between hover:border-neutral-700/80 transition-all duration-300">

                                    <!-- Premium Glassmorphic Layer -->
                                    <div class="absolute inset-0 bg-[linear-gradient(to_bottom_right,rgba(24,24,27,0.6),rgba(9,9,11,0.9))] bg-[radial-gradient(#262626_1px,transparent_1px)] [background-size:16px_16px] transition-all duration-500 group-hover:scale-105" />

                                    <!-- Top Utility Row -->
                                    <div class="relative z-10 flex justify-between items-center w-full">
                                        <span class="text-[9px] bg-neutral-950/90 backdrop-blur-sm px-2 py-0.5 rounded border border-neutral-800 font-mono text-neutral-400 tracking-tight">
                                            clip_v{{ asset.id }}
                                        </span>
                                        <span class="text-[9px] bg-purple-950/60 text-purple-400 px-1.5 py-0.5 rounded border border-purple-900/30 font-medium">
                                            {{ asset.tag }}
                                        </span>
                                    </div>

                                    <!-- Waveform Indicator Placeholder -->
                                    <div class="relative z-10 flex items-center justify-center gap-1.5 h-6 opacity-30 group-hover:opacity-100 transition duration-300">
                                        <span class="text-xl mr-1">{{ aiFeatures[activeTab].icon }}</span>
                                        <div class="w-1 h-3 bg-white rounded-full animate-pulse" />
                                        <div class="w-1 h-5 bg-purple-500 rounded-full animate-pulse [animation-delay:0.2s]" />
                                        <div class="w-1 h-4 bg-white rounded-full animate-pulse [animation-delay:0.4s]" />
                                    </div>

                                    <!-- Bottom Row Controls & Video Track Bar -->
                                    <div class="relative z-10 w-full space-y-2">
                                        <div class="w-full bg-neutral-800 h-1 rounded-full overflow-hidden">
                                            <div class="bg-gradient-to-r from-purple-500 to-pink-500 h-full w-1/3 group-hover:w-full transition-all duration-1000 ease-out" />
                                        </div>

                                        <div class="flex items-center justify-between">
                                            <span class="text-[10px] font-mono text-neutral-500">{{ asset.duration }}</span>

                                            <div class="opacity-0 group-hover:opacity-100 transition-all duration-200 translate-y-1 group-hover:translate-y-0">
                                                <button @click="openAlertModal('Timeline Push', 'Asset successfully cached. In the production app, this layout asset bridges natively directly into Adobe Premiere Pro or DaVinci Resolve.')" class="bg-white text-black font-bold text-[10px] px-2.5 py-1 rounded shadow-md hover:bg-neutral-200 transition">
                                                    Add to Edit
                                                </button>
                                            </div>
                                        </div>
                                    </div>

                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- Pricing / Plan Section -->
        <section id="pricing" class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 py-20 sm:py-28 scroll-mt-20">
            <div class="text-center mb-12">
                <h2 class="text-3xl sm:text-5xl font-bold tracking-tight mb-4">Simple, straightforward pricing.</h2>
                <p class="text-neutral-400 max-w-md mx-auto mb-8">Get full access to all design tool extensions and asset marketplaces instantly.</p>

                <div class="inline-flex items-center gap-3 bg-neutral-900 p-1 rounded-full border border-neutral-800">
                    <button @click="isAnnual = false" :class="[!isAnnual ? 'bg-purple-600 text-white' : 'text-neutral-400']" class="px-4 py-1.5 rounded-full text-xs font-bold transition">
                        Monthly
                    </button>
                    <button @click="isAnnual = true" :class="isAnnual ? 'bg-purple-600 text-white' : 'text-neutral-400'" class="px-4 py-1.5 rounded-full text-xs font-bold transition">
                        Annual (Save 20%)
                    </button>
                </div>
            </div>

            <div class="max-w-sm mx-auto rounded-3xl border-2 border-purple-500 bg-gradient-to-b from-purple-950/10 to-neutral-950 p-8 relative shadow-2xl">
                <div class="absolute -top-4 left-1/2 -translate-x-1/2 px-4 py-1 rounded-full bg-purple-500 text-white font-bold text-xs tracking-wide uppercase">
                    All-Access Pass
                </div>

                <div class="text-center mb-6">
                    <h3 class="text-2xl font-extrabold text-white mb-2">Creator Membership</h3>
                    <div class="mt-4 flex items-baseline justify-center gap-1">
                        <span class="text-5xl font-black text-white tracking-tight">
                            {{ isAnnual ? '$29' : '$39' }}
                        </span>
                        <span class="text-neutral-400 text-sm">/ mo</span>
                    </div>
                    <p v-if="isAnnual" class="text-xs text-purple-400 mt-2 font-medium">Billed annually ($348)</p>
                </div>

                <hr class="border-neutral-900 my-6" />

                <ul class="space-y-4 mb-8 text-sm text-neutral-300">
                    <li class="flex items-center gap-3"><span class="text-purple-400">✓</span> Unlimited Asset Downloads</li>
                    <li class="flex items-center gap-3"><span class="text-purple-400">✓</span> Full Commercial Usage License</li>
                    <li class="flex items-center gap-3"><span class="text-purple-400">✓</span> Adobe & DaVinci Panel Extensions</li>
                    <li class="flex items-center gap-3"><span class="text-purple-400">✓</span> Generation credits for Veo & Nano Banana</li>
                </ul>

                <button @click="openAlertModal('Membership Checkout', 'Audition checkpoint reached! This link would normally establish a billing agreement session via Stripe.')" class="w-full inline-flex items-center justify-center py-4 px-6 font-bold rounded-xl bg-white text-black hover:bg-neutral-200 transition">
                    Start Your Membership
                </button>
            </div>
        </section>

        <!-- Global Alert Modal Block -->
        <div v-if="isAlertOpen" class="fixed inset-0 z-50 flex items-center justify-center px-4">
            <!-- Backdrop -->
            <div @click="closeAlertModal" class="absolute inset-0 bg-neutral-950/80 backdrop-blur-sm" />

            <!-- Modal Box -->
            <div class="relative w-full max-w-sm rounded-2xl border border-neutral-800 bg-neutral-900 p-6 shadow-2xl animate-in fade-in zoom-in-95 duration-200">
                <h3 class="text-lg font-bold text-white mb-2">{{ alertTitle }}</h3>
                <p class="text-sm text-neutral-400 leading-relaxed mb-6">{{ alertMessage }}</p>
                <button @click="closeAlertModal" class="w-full bg-neutral-800 hover:bg-neutral-700 text-white font-semibold py-2.5 px-4 rounded-xl transition text-sm">
                    Acknowledge
                </button>
            </div>
        </div>

        <!-- Simple Footer -->
        <footer class="border-t border-neutral-900 bg-neutral-950 py-8 text-center text-xs text-neutral-600">
            <p>&copy; 2026 PromptEdit Pro Redesign Audition Page.</p>
        </footer>

    </div>
</template>
