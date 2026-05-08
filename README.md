<div align="center">

# shopNG

**Nigeria's modern e-commerce web app — built with Angular 19, Signals and standalone components.**

[![Angular](https://img.shields.io/badge/Angular-19-red?style=for-the-badge&logo=angular)](https://angular.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)](https://typescriptlang.org)
[![Products](https://img.shields.io/badge/Products-50-purple?style=for-the-badge)](/)

Authored by **Gamaliel Egbuchiri**

</div>

---

| | |
|---|---|
| **Framework** | Angular 19 — standalone components |
| **Language** | TypeScript 5 |
| **State** | Angular Signals — signal, computed, effect |
| **Products** | 50 items across 6 categories |
| **Pages** | Home · Products · Detail · Cart · Checkout · Account |
| **Search** | Live full-text search with 350ms debounce |

---

## Introduction

shopNG is a fully functional online store designed and built for the Nigerian market. The app features 50 real products across 6 categories, all priced in Nigerian Naira (₦). It has a live search that works instantly as you type, a 3-step checkout process, cart management with VAT calculations, a wishlist, and an account page showing order history.

The project is built entirely with Angular 19's newest features — standalone components mean there are no NgModules anywhere in the codebase. All reactive state is managed using Angular Signals, which removes the need for any external state management library like NgRx. All 6 routes are lazy-loaded, meaning only the page the user navigates to is downloaded at that moment.

The UI uses real product photographs sourced from Unsplash, a custom purple design system, and automatically adapts to dark mode using CSS custom properties and `prefers-color-scheme`.

---

## Table of Contents

- [The 50 Products](#the-50-products)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [UI / UX Design](#ui--ux-design)

---

## The 50 Products

| Category | Items |
|---|---|
| **Electronics** | Smartphones · Earbuds · Laptops · Smartwatches · Power Banks · Charging Cables · Bluetooth Speakers · Phone Cases · Smart Home Gadgets · Laptop Bags |
| **Clothing** | T-shirts · Leggings · Hoodies · Underwear · Sneakers · Jeans · Loungewear · Handbags · Jackets · Dresses |
| **Beauty** | Face Serums · Cleansers · Lotions · Shampoo · Makeup · Deodorant · Sunscreen · Pimple Patches · Toothpaste · Diffusers |
| **Home** | Water Bottles · Air Fryers · Office Chairs · Desk Organizers · Desk Lamps · Bedding · Curtains · Coffee · Doorbells · Kitchen Utensils |
| **Sports** | Yoga Mats · Resistance Bands · Vitamins · Sunglasses · Safety Alarms |
| **Others** | Pet Food · Cleaning Supplies · Video Games · Board Games · Car Accessories |

---

## How to Run

```bash
npm install
ng serve
```

Open **http://localhost:4200** in your browser.

```bash
# Production build
ng build --configuration=production
```

---

## Project Structure

```
src/
├── app/
│   ├── components/
│   │   ├── navbar/              Sticky nav — search bar, cart badge, icons
│   │   └── product-icon/        SVG fallback icon when image fails to load
│   ├── models/
│   │   └── product.model.ts     Product · CartItem · Review · Order types
│   ├── pages/
│   │   ├── home/                Hero · category grid · 8 featured products
│   │   ├── products/            50 items · live search · filter · sort
│   │   ├── product-detail/      Full product · qty selector · wishlist
│   │   ├── cart/                Cart items · quantity controls · VAT summary
│   │   ├── checkout/            3-step: delivery → payment → confirm
│   │   └── account/             Orders · wishlist · addresses · settings
│   ├── services/
│   │   ├── product.service.ts   50 products and full-text search logic
│   │   ├── cart.service.ts      Signals-based reactive cart state
│   │   └── wishlist.service.ts  Signals-based wishlist state
│   ├── app.component.html       Navbar + router-outlet
│   ├── app.config.ts            App providers and routing config
│   └── app.routes.ts            6 lazy-loaded route definitions
├── styles.scss                  Global styles and CSS custom properties
└── index.html                   App shell
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Angular 19 — standalone components, no NgModules |
| Language | TypeScript 5 |
| State | Angular Signals — signal, computed, effect |
| Routing | Angular Router with lazy loading and View Transitions API |
| Styling | Component-scoped SCSS and CSS custom properties |
| Images | Real product photos via Unsplash |
| Fonts | DM Sans via Google Fonts |
| Search | Client-side full-text, debounced, reactive |

---

## UI / UX Design

The following pages show the actual rendered UI of the application. Each screen is a screenshot taken directly from the running app in the browser.

### Design System

| Token | Value | Used For |
|---|---|---|
| Primary accent | `#534AB7` | Buttons, active states, badges, focus rings |
| Background | `#F5F5F7` | Page background |
| Surface | `#FFFFFF` | Cards, navbar, sidebar panels |
| Border | `#E5E5EA` | Card outlines, dividers, input borders |
| Text primary | `#1A1A1A` | Headings and main body text |
| Text muted | `#6E6E73` | Labels, meta, descriptions |

---

### Page 1 — Home

The entry point of the app. Shows a hero banner with a discount badge, a 6-category grid, 8 featured product cards with real photos, and a trust strip.

![Home page — hero banner, category grid, featured product cards] [![Play Game](https://img.shields.io/badge/Play-Live_Demo-green?style=for-the-badge&logo=googlechrome)](shopng-Account.png)
| | |
|---|---|
| **Hero banner** | Purple brand colour with "40% off" badge and free delivery message. |
| **Category grid** | 6 categories shown as icon cards. Tap any to filter the products page. |
| **Product cards** | Real Unsplash photos with sale/new badges overlaid. Add to cart on the card. |
| **Trust strip** | Secure checkout, fast delivery, 30-day returns, 24/7 support. |

---

### Page 2 — Products with live search

50 products in a 3-column grid. The filter sidebar lets users narrow by category, price range and rating. The search bar in the navbar triggers live results as you type.

![Products page — filter sidebar, live search banner, product grid](shopng_all_pages_uiux.html - Google Chrome 5_7_2026 7_03_35 AM.png)

| | |
|---|---|
| **Live search** | Triggers after 350ms debounce. A purple banner confirms the active query with a clear button. |
| **Filters** | Category checkboxes, price slider and star rating all work on top of search results simultaneously. |
| **Category chips** | Quick-tap filters shown above the grid that match the sidebar checkboxes. |
| **Sort dropdown** | Popular, price low-high, price high-low, top rated, A–Z. |

---

### Page 3 — Product detail

Full product view with large photo, pricing with savings shown in green, description, quantity selector, add to cart, wishlist toggle and customer reviews.

![Product detail page — large photo, price, add to cart, reviews](shopng_all_pages_uiux.html - Google Chrome 5_7_2026 7_05_10 AM.png)

| | |
|---|---|
| **Price display** | Original price struck through, discount badge top-left, savings amount shown in green. |
| **Quantity selector** | Inline minus/plus buttons before the add-to-cart action. |
| **Free delivery badge** | Shown below the action buttons to reassure at the point of decision. |
| **Reviews** | Customer reviews with avatar initials, star rating and date shown in a 2-column grid. |

---

### Page 4 — Cart

All cart items with real product thumbnails, inline quantity controls, item totals and a sticky order summary panel with transparent VAT breakdown.

![Cart page — product thumbnails, qty controls, VAT breakdown, order summary](shopng_all_pages_uiux.html - Google Chrome 5_7_2026 7_07_29 AM.png)

| | |
|---|---|
| **Item thumbnails** | Real product photos pulled from the same Unsplash source as the product cards. |
| **VAT breakdown** | Subtotal, delivery, 7.5% VAT and total shown separately so the user sees exactly what they pay. |
| **Free delivery** | Automatically applied and shown in green when subtotal exceeds ₦50,000. |
| **Order summary** | Sticky right panel with checkout button and continue shopping link. |

---

### Page 5 — Checkout

A clean 3-step checkout flow. Delivery address with Nigerian format fields, then payment method selection (card, bank transfer, USSD), then order confirmation.

![Checkout page — 4-step progress bar, delivery form, payment options](shopng_all_pages_uiux.html - Google Chrome 5_7_2026 7_08_59 AM.png)

| | |
|---|---|
| **4-step progress bar** | Cart → Delivery → Payment → Confirm. The current step is highlighted in purple. |
| **Nigerian address form** | First name, last name, street, city, state, and Nigerian phone number format. |
| **Payment options** | Debit/credit card (Visa, Mastercard, Verve), bank transfer, USSD codes. |
| **Order total** | Shown at the bottom of the form before the final Place Order button. |

---

### Page 6 — Account

User profile page with 4 tabs — Orders, Wishlist, Addresses and Settings. Order history shows product thumbnails, amounts and colour-coded status badges.

![Account page — profile header, order history, status badges](shopng_all_pages_uiux.html - Google Chrome 5_7_2026 7_10_33 AM.png)

| | |
|---|---|
| **Profile header** | Purple banner with user initials avatar, full name and email address. |
| **Order history** | Product thumbnail, order number, amount in ₦ and date for each order. |
| **Status badges** | Delivered (green), In transit (amber), Processing (purple). |
| **Tab navigation** | Orders, Wishlist, Addresses and Settings all accessible from this single page. |

---

<div align="center">

**Gamaliel Egbuchiri**

*shopNG — The best deals, delivered to you.*

</div>
