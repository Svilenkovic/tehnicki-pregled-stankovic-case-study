<a href="https://stankovic964.rs/"><img src="media/cover.jpg" alt="Tehnički Pregled Stanković 964, home page on a laptop and a phone" width="100%"></a>

# Tehnički Pregled Stanković 964

Five-page site for a vehicle inspection station near Aleksinac, made for a quick call from the car, plus a private inventory PWA with live sync.

**[stankovic964.rs](https://stankovic964.rs/)** · [Case study (in Serbian)](https://svilenkovic.com/radovi/tehnicki-pregled-stankovic) · [App page](https://svilenkovic.com/en/aplikacija-tehnicki-pregled) · [Srpski](README.sr.md)

> [!NOTE]
> Client project. The source code belongs to the client and stays in a private repository. This page describes what I built and how.

<table>
  <tr><td><b>Client</b></td><td>Tehnički Pregled Stanković 964</td></tr>
  <tr><td><b>Industry</b></td><td>Licensed vehicle inspection station</td></tr>
  <tr><td><b>Location</b></td><td>Pertate, Aleksinac, Serbia</td></tr>
  <tr><td><b>Type</b></td><td>Multi-page website with an inventory PWA</td></tr>
  <tr><td><b>My role</b></td><td>Design, development, SEO, hosting and maintenance</td></tr>
  <tr><td><b>Stack</b></td><td>PHP 8.3, nginx cache, MariaDB, PWA, Server-Sent Events</td></tr>
</table>

## About the project

Tehnički Pregled Stanković 964 inspects cars, light trucks up to 2.5 t and trailers in Pertate near Aleksinac, and fixes vehicle lights on the spot. Nobody books ahead; people turn up during working hours, so the first screen answers what they would otherwise ask by phone and offers two numbers to call with one tap.

The first check after launch showed the page jumping badly while it loaded (a layout shift above 1), and it took three separate fixes to stop it. The main CSS had been deferred, so the page painted unstyled and then reflowed. The counters on the home page counted up from zero and changed width, and the fallback font had different proportions from the web font. Now the CSS loads normally, the numbers are static and the fallback font has metrics that match.

## What I built

- A price page that lists the services and what an inspection covers without printing amounts, because the official price list changes
- A contact map that had been showing another company in another town, replaced with a query for the station's own address, postcode and municipality
- Caching in nginx switched back on after an old rule added no-cache to every CSS, JS and PHP response and matched before the PHP block
- Nine CSS files merged into one, and a small main.js with IntersectionObserver instead of any library
- A private inventory PWA for items, categories, quantities, prices and change history, synced live across devices over SSE with a polling fallback
- Panel login with bcrypt, CSRF tokens, a 30-minute lock after five failed attempts counted per user and per address, idle and total session limits and a device log

## Results

| | Performance | Accessibility | Best practices | SEO |
| :-- | :-: | :-: | :-: | :-: |
| Mobile | 88 | 100 | 100 | 100 |
| Desktop | 99 | 100 | 100 | 100 |

PageSpeed Insights, lab test of the live site, September 2026. Security headers: 6 of 6. HTML validator: no errors. axe accessibility check: no violations. Structured data: `AutomotiveBusiness`.

## Screenshots

<table>
  <tr>
    <td width="68%" valign="top"><img src="media/desktop.webp" alt="Tehnički Pregled Stanković 964, home page on a 1440 px screen"></td>
    <td width="32%" valign="top"><img src="media/mobile.webp" alt="Tehnički Pregled Stanković 964, home page on a phone"></td>
  </tr>
</table>

<img src="media/inner-1.webp" alt="Four inspection types in the &quot;Sve na jednom mestu&quot; (Everything in one place) section">
<sub>Four inspection types in the "Sve na jednom mestu" (Everything in one place) section</sub>

<img src="media/inner-2.webp" alt="About the station and opening hours for each day">
<sub>About the station and opening hours for each day</sub>

---

<sub>Built by [D. Svilenković](https://svilenkovic.com).</sub>
