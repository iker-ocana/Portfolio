<template>
    <svg class="border-top-svg" width="300" height="300" xmlns="http://www.w3.org/2000/svg" style="pointer-events:none">
        <defs>
            <linearGradient id="svggradient-top" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" class="gradient1" /> /* Red at 0% */
                <stop offset="50%" class="gradient2" /> /* Blue at 50% */
                <stop offset="100%" class="gradient3" /> /* Magenta at 100% *
            </linearGradient>
        </defs>
        <path fill="url('#svggradient-top')" d="M8 0h292l-20 20H25a5 5 0 0 0-5 5v255L0 300V8a8 8 0 0 1 8-8Z">
        </path>
    </svg>
</template>