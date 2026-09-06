# Resolve Performance & Recovery

A responsive Vue 3 and Vite website for Resolve Performance & Recovery.

## Requirements

- Node.js 20 or newer
- npm

## Run locally

~~~bash
npm install
npm run dev
~~~

Open the local URL displayed by Vite.

## Production build

~~~bash
npm run build
~~~

The production-ready files are created in dist/.

## Connect MassageBook and credit-card payments

Open src/App.vue and update these values near the top of the script:

~~~js
const bookingUrl = ''
const paymentUrl = ''
~~~

- bookingUrl: Your public MassageBook booking or embeddable scheduling URL.
- paymentUrl: Your secure hosted checkout or membership-payment URL.

Card information should be collected by MassageBook, Stripe, Square, or another PCI-compliant hosted processor—not directly by this static website.

Some providers prevent their pages from being displayed inside an iframe. If MassageBook blocks embedding, the booking buttons will still work by opening the booking URL in a new browser tab.

## Main files

- src/App.vue — page content and interactions
- src/styles.css — responsive design and branding
- src/main.js — Vue application entry point
- public/hero-recovery.jpg — homepage hero image
- index.html — document metadata and application mount point
# resolverecover
