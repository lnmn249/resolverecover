<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

// Replace these two values with the links supplied by MassageBook and your payment provider.
const bookingUrl = 'https://www.massagebook.com/biz/resolve-performance-and-recovery'
const paymentUrl = 'https://www.massagebook.com/biz/resolve-performance-and-recovery'
const membershipUrl =
  'https://www.massagebook.com/therapists/resolve-performance-and-recovery/deals?src=external'
const serviceLinks = {
  targeted:
    'https://www.massagebook.com/business/39250220/booking/?service_id=2096237&src=external',

  full:
    'https://www.massagebook.com/business/39250220/booking/?service_id=2096240&src=external',

  onsite:
    'https://www.massagebook.com/business/39250220/booking/?service_id=2096241&src=external',

  membership:
    'https://www.massagebook.com/therapists/resolve-performance-and-recovery/deals?src=external'
}
const instagramUrl =
  'https://www.instagram.com/energypathsllc/'
const menuOpen = ref(false)
const bookingOpen = ref(false)

const currentYear = new Date().getFullYear()

const services = [
  {
    number: '01',
    name: 'Targeted Resolve',
    time: '60 minutes',
    price: '$100',
    description: 'Focused therapeutic massage for one primary problem area and the muscular patterns connected to it.',
    tags: ['Upper body', 'Lower body', 'Post-workout'],
    bookingKey: 'targeted',
  },
  {
    number: '02',
    name: 'Full Resolve',
    time: '90 minutes',
    price: '$150',
    description: 'Comprehensive therapeutic massage for multiple problem areas or full-body athletic recovery.',
    tags: ['Multiple areas', 'Extended work', 'Full recovery'],
    bookingKey: 'full',
  },
  {
    number: '03',
    name: 'Resolve On-Site',
    time: '90 minutes',
    price: '$250',
    description: 'Mobile therapeutic massage and recovery brought to your home, office, or training location in the Waukesha area.',
    tags: ['Local travel', 'Table setup', 'Customized'],
    bookingKey: 'onsite',
  },
]

const focusAreas = [
  ['Shoulders & arms', 'Overuse, limited motion, and persistent muscular tension'],
  ['Upper back & neck', 'Connected patterns affecting comfort and everyday movement'],
  ['Hips & glutes', 'Targeted work supporting the legs, pelvis, and lower back'],
  ['Hamstrings & legs', 'Post-workout fatigue, tightness, and lower-body recovery'],
]

function scrollTo(id) {
  menuOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

function openBooking() {
  if (bookingUrl) window.open(bookingUrl, '_blank', 'noopener,noreferrer')
  else bookingOpen.value = true
}

function openPayment() {
  if (paymentUrl) window.open(paymentUrl, '_blank', 'noopener,noreferrer')
  else bookingOpen.value = true
}

function openMembership() {
  window.open(membershipUrl, '_blank', 'noopener,noreferrer')
}

function closeOnEscape(event) {
  if (event.key === 'Escape') bookingOpen.value = false
}

function openService(serviceName) {
  const url = serviceLinks[serviceName]

  if (url) {
    window.location.href = url
  }
}
onMounted(() => window.addEventListener('keydown', closeOnEscape))
onBeforeUnmount(() => window.removeEventListener('keydown', closeOnEscape))
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="#top" aria-label="Resolve Performance and Recovery home">
        <span class="brand-mark" aria-hidden="true"><i></i><i></i></span>
        <span><strong>RESOLVE</strong><small>PERFORMANCE &amp; RECOVERY</small></span>
      </a>

      <button class="menu-button" type="button" :aria-expanded="menuOpen" aria-label="Toggle navigation" @click="menuOpen = !menuOpen">
        <span></span><span></span>
      </button>

      <nav :class="{ open: menuOpen }" aria-label="Main navigation">
        <button type="button" @click="scrollTo('approach')">Approach</button>
        <button type="button" @click="scrollTo('about-dale')">Meet Dale</button>
        <button type="button" @click="scrollTo('services')">Services</button>
        <button type="button" @click="scrollTo('membership')">Membership</button>
        <button class="nav-cta" type="button" @click="openBooking">Book a session</button>
      </nav>
      
    </header>

    <main id="top">
      <section class="hero">
        <div class="hero-image" aria-hidden="true"></div>
        <div class="hero-shade" aria-hidden="true"></div>
        <div class="hero-content">
          <p class="eyebrow"><span></span> Focused therapeutic bodywork</p>
          <h1>Move better.<br><em>Recover stronger.</em></h1>
          <p class="hero-copy">Focused therapeutic massage and bodywork in Waukesha, Wisconsin for athletes, active adults, and anyone ready to address muscular tension, overuse, or restricted movement.</p>
          <div class="hero-actions">
            <button class="button primary" type="button" @click="openBooking">Book your session <span>↗</span></button>
            <button class="text-link" type="button" @click="scrollTo('services')">Explore services <span>↓</span></button>
          </div>
        </div>
        <div class="hero-note"><strong>Specialized focus</strong><span>Arms · Shoulders · Upper back · Neck</span></div>
      </section>

      <section id="approach" class="approach section-pad">
        <div class="section-kicker">THE APPROACH</div>
        <div class="approach-grid">
          <h2>Not a standard routine.<br><span>Work built around you.</span></h2>
          <div class="approach-copy">
            <p>Each session begins with a conversation about where you would like the focus to be that day. </p>
              
            <p>From there, the work is tailored to what you are noticing and what your body needs rather than limited to a standard routine.</p>
            
          </div>
        </div>

        <div class="process-row">
          <article><b>01</b><h3>Assess</h3><p>Start with your focus, your movement, and the outcome you want.</p></article>
          <article><b>02</b><h3>Target</h3><p>Focus the session on the primary area and its connected patterns.</p></article>
          <article><b>03</b><h3>Resolve</h3><p>Leave with less restriction and a clearer path back to activity.</p></article>
        </div>
      </section>
        <section id="about-dale" class="practitioner section-pad">
  <div class="practitioner-photo">
    <img
      src="/dale-hartung.jpg"
      alt="Dale Hartung, practitioner at Resolve Performance and Recovery"
    />

    <div class="photo-label">
      <strong>Dale Hartung</strong>
      <span>Resolve Performance &amp; Recovery</span>
    </div>
  </div>

  <div class="practitioner-content">
    <div class="section-kicker">MEET THE PRACTITIONER</div>

    <p class="personal-tagline">
      Focused hands. Intentional work. Better movement.
    </p>

    <h2>Meet <span>Dale.</span></h2>

    <div class="bio-copy">
      <p>
        I provide focused therapeutic bodywork for athletes, active adults,
        and anyone experiencing muscular tension, overuse, restricted
        movement, or difficulty recovering from physical activity. I primarily work
        in Waukesa, Wisconsin, but I also provide on-site sessions for local clients in the area.
      </p>

      <p>
        Each session begins with a conversation about where you would like the focus to be that day. 
        From there, the work is tailored to what you are noticing and what your body 
        needs rather than limited to a standard routine.
      </p>

      <p>
        I specialize in detailed work involving the arms, shoulders, upper
        back, and neck. I also provide focused lower-body recovery work for
        the hips, gluteal muscles, quadriceps, hamstrings, and calves.
      </p>

      <p>
        My interest in the body extends beyond muscles and movement. I began
        exploring energy practices in 2007 and have trained in both Reiki and
        neigong. These practices bring greater attention to breath, stillness,
        internal awareness, and energetic balance. They may remain a subtle
        influence or be incorporated more intentionally when requested.
      </p>

      <p>
        Whether you are recovering from a demanding workout, managing a
        persistent trouble spot, or simply trying to feel more capable in your
        body, my objective is straightforward: better movement, stronger
        recovery, and meaningful results.
      </p>
    </div>
  </div>
</section>
      <section class="focus section-pad">
        <div class="focus-heading">
          <div>
            <div class="section-kicker light">AREAS OF FOCUS</div>
            <h2>Connected work.<br><span>Whole-body results.</span></h2>
          </div>
          <p>From the shoulders to the hamstrings, the goal is straightforward: focused work that helps your body function better.</p>
        </div>
        <div class="focus-list">
          <article v-for="(area, index) in focusAreas" :key="area[0]">
            <span>0{{ index + 1 }}</span><h3>{{ area[0] }}</h3><p>{{ area[1] }}</p>
          </article>
        </div>
      </section>

      <section id="services" class="services section-pad">
        <div class="section-kicker">SERVICES</div>
        <div class="section-title-row">
          <h2>Choose the time.<br><span>We’ll focus the work.</span></h2>
          <p>You do not need to choose a technique. Tell me what is happening and what you want to get back to.</p>
        </div>
        <div class="service-grid">
          <article v-for="service in services" :key="service.name" class="service-card">
            <div class="service-top"><span>{{ service.number }}</span><span>{{ service.time }} · {{ service.price }}</span></div>
            <h3>{{ service.name }}</h3>
            <p>{{ service.description }}</p>
            <div class="tags"><span v-for="tag in service.tags" :key="tag">{{ tag }}</span></div>
            <button
              class="service-link"
              type="button"
              @click="openService(service.bookingKey)"
            >
              Book {{service.name}} <span>↗</span>
            </button>
          </article>
        </div>
      </section>

      <section id="membership" class="membership section-pad">
        <div class="membership-card">
          <div class="membership-copy">
            <div class="section-kicker light">MONTHLY MAINTENANCE</div>
            <h2>Stay<br><em>Resolved.</em></h2>
            <p>One monthly 60-minute Targeted Resolve session for clients who train regularly, perform physically demanding work, or want to stay ahead of recurring tension.</p>
            <!-- <button class="button outline" type="button" @click="openPayment">Join the membership <span>↗</span></button> -->
             <button
                class="button outline"
                type="button"
                @click="openService('membership')"
              >
                View membership <span>↗</span>
              </button>
          </div>
          <div class="membership-details">
            <div><span>Monthly price</span><strong>$80/month</strong></div>
            <div><span>Included monthly</span><strong>1 Targeted Resolve</strong></div>
            <div><span>Session length</span><strong>60 minutes</strong></div>
            <div><span>Unused session</span><strong>Rolls over 1 month</strong></div>
            <small>Membership renews monthly. Full Resolve and on-site sessions are not included.</small>
          </div>
        </div>
      </section>

      <section id="booking" class="booking section-pad">
        <div class="booking-copy">
          <div class="section-kicker">BOOKING &amp; PAYMENT</div>
          <h2>Ready to get<br><span>back to movement?</span></h2>
          <p>Choose your session and complete booking and payment securely through the online booking portal.</p>
          <button class="button primary dark" type="button" @click="openBooking">Open booking portal <span>↗</span></button>
          <small>Secure scheduling and payment powered by your booking provider.</small>
        </div>
        <div class="embed-shell">
  <div class="embed-ready massagebook-embed">
  <iframe
    src="https://www.massagebook.com/therapists/resolve-performance-and-recovery/widget/services"
    title="Book a service with Resolve Performance and Recovery"
  ></iframe>
</div>
</div>
      </section>
    </main>

    <footer class="site-footer">
  <div class="footer-main">
    <div class="footer-brand">
      <a
        class="footer-logo"
        href="#top"
        aria-label="Resolve Performance and Recovery home"
      >
        <span class="footer-mark">R</span>

        <span class="footer-name">
          <strong>RESOLVE</strong>
          <small>PERFORMANCE &amp; RECOVERY</small>
        </span>
      </a>

      <p>
        Targeted bodywork. Better movement.<br />
        Stronger recovery.
      </p>
    </div>

    <div class="footer-column">
      <strong>Explore</strong>

      <a href="#approach">Approach</a>
      <a href="#about-dale">Meet Dale</a>
      <a href="#services">Services</a>
      <a href="#membership">Membership</a>
    </div>

    <div class="footer-column">
      <strong>Visit</strong>

      <a
        href="https://www.google.com/maps/search/?api=1&query=804+N+Grand+Ave%2C+Waukesha%2C+WI+53186"
        target="_blank"
        rel="noopener noreferrer"
      >
        804 N Grand Ave<br />
        Waukesha, WI 53186
      </a>

      <p class="arrival-note">
    Located inside Topaz Apothecary.<br />
    The entrance may be locked—text when you arrive.
  </p>

      <a href="tel:+12623704314">
        (262) 370-4314
      </a>
    </div>
     <a
  class="instagram-button"
  href="https://www.instagram.com/energypathsllc/"
  target="_blank"
  rel="noopener noreferrer"
  aria-label="Energy Paths LLC on Instagram"
>
  <svg
    viewBox="0 0 24 24"
    aria-hidden="true"
  >
    <rect x="3" y="3" width="18" height="18" rx="5"></rect>
    <circle cx="12" cy="12" r="4"></circle>
    <circle class="instagram-dot" cx="17.5" cy="6.5" r="1"></circle>
  </svg>

  <span>
    <small>Follow on Instagram</small>
    @energypathsllc
  </span>
</a>

    <div class="footer-action">
      <span>Ready to move better?</span>

      <a class="button footer-button" href="#booking">
        Book a session <span>↗</span>
      </a>
    </div>
  </div>

  <div class="footer-bottom">
    <span>
      © {{ currentYear }} Resolve Performance &amp; Recovery
    </span>

    <a href="https://resolverecoverywi.com">
      resolverecoverywi.com
    </a>
  </div>
</footer>

    <div v-if="bookingOpen" class="modal-backdrop" role="presentation" @click.self="bookingOpen = false">
      <section class="modal" role="dialog" aria-modal="true" aria-labelledby="modal-title">
        <button class="modal-close" type="button" aria-label="Close" @click="bookingOpen = false">×</button>
        <span class="modal-mark">R</span>
        <h2 id="modal-title">One link away.</h2>
        <p>The site is ready for your live MassageBook booking or hosted payment link. Add those URLs before launch and every booking button will connect securely.</p>
        <button class="button primary dark" type="button" @click="bookingOpen = false">Got it</button>
      </section>
    </div>
  </div>
</template>
