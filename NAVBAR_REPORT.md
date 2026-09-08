# Navbar / Mobile Drawer Report

## Overview

Ye report Shopify theme ke navbar mobile drawer implementation par based hai. Main file `snippets/header-drawer.liquid` hai, jo mobile menu drawer render karti hai. Drawer top header ke menu icon se open hota hai, submenu navigation support karta hai, aur custom Gemora mobile design enabled hone par card-style navigation UI dikhata hai.

## Primary File

- `snippets/header-drawer.liquid`

Ye snippet `linklist`, `block`, aur `section` settings use karke drawer menu generate karta hai. Isme markup, Liquid logic, accessibility attributes, CSS variables, localization links, featured products/collections, aur drawer-specific CSS included hai.

## Supporting Files

- `assets/header-drawer.js`
- `snippets/mobile-drawer-card-content.liquid`
- `snippets/mobile-drawer-submenu-header.liquid`
- `snippets/mobile-drawer-submenu-link-content.liquid`

`header-drawer.js` drawer open/close, back action, Escape key close, focus trap, submenu state, aur animation cleanup handle karta hai. Mobile drawer snippets custom Gemora cards, submenu banner, icons, fallback images, aur category-specific styling data render karte hain.

## Current Functionality

Navbar drawer me ye main features available hain:

- Hamburger menu se drawer open/close hota hai.
- Close button aur Escape key support available hai.
- Menu links 1-level, 2-level, aur 3-level structures ke liye render hote hain.
- Accordion mode aur flat menu mode dono supported hain.
- First accordion item auto-open setting supported hai.
- Active page links ke liye `aria-current="page"` use hota hai.
- Submenus ke liye back button aur close button available hain.
- Featured collections aur featured products drawer me show kiye ja sakte hain.
- Localization selector drawer ke utility area me supported hai.
- Section Rendering API ke case me heavy featured product data eager load hota hai.

## Custom Gemora Mobile Design

Custom design `block_settings.mobile_drawer_custom_design` setting se enable hota hai. Enable hone par:

- Root element me `header-drawer--gemora` class add hoti hai.
- Drawer panel me `menu-drawer--gemora` class add hoti hai.
- Brand header logo ya fallback gem icon + title/subtitle render hota hai.
- Main links card layout me display hote hain.
- Categories jaise Home, Gemstones, Precious, Semi Precious, Jewellery, Sale, More, aur Support ke liye custom icons/backgrounds set hote hain.
- Gemstones, Precious, Semi Precious, aur Jewellery jaise categories ke liye fallback images use hote hain.
- Submenu ke top me banner style header dikhaya jata hai.
- Submenu links image icons ya Bootstrap icon fallback ke saath render hote hain.

## Styling Summary

Drawer CSS same `header-drawer.liquid` file ke stylesheet block me present hai. Important styling points:

- Gemora drawer width `min(93vw, 340px)` rakhi gayi hai.
- Drawer background warm light gradient style me hai.
- Menu cards compact hain, around 54px minimum height ke saath.
- Submenu items 46px minimum height ke saath compact list layout me hain.
- Icon size, font size, card radius, text color, aur background colors CSS variables se control hote hain.
- Plus icon ko custom chevron-style visual me convert kiya gaya hai.
- Hover transitions close button aur icons par added hain.

## Accessibility Notes

Implementation me accessibility ke liye kuch achhe points already present hain:

- Menu summary button par translated `aria-label` use hota hai.
- Drawer navigation me `aria-label` available hai.
- Active links me `aria-current="page"` set hota hai.
- Open/close actions me `aria-expanded` update hota hai.
- JavaScript focus trap use karta hai, jisse keyboard users drawer ke andar focused rahte hain.
- Escape key drawer close karti hai.
- Decorative icons par `aria-hidden="true"` use kiya gaya hai.

## Performance Notes

- `header-drawer.js` module `fetchpriority="low"` ke saath load hota hai.
- Heavy featured product/collection content initial render me avoid kiya gaya hai, jab tak Section Rendering API render case detect na ho.
- Drawer images mostly constrained widths ke saath load hoti hain.
- Submenu icon images lazy load hoti hain.

## Potential Improvements

- Custom Gemora design Bootstrap icon classes (`bi ...`) use karta hai. Confirm karna chahiye ki Bootstrap Icons theme me globally loaded hain.
- Fallback image asset names verify karne chahiye, especially `mobile-drawer-semi-precious-top-banner.png` aur all `mega-menu-*` icons.
- Custom CSS me kuch hard-coded colors hain. Future maintainability ke liye inhe theme settings ya shared CSS variables me move kiya ja sakta hai.
- Submenu banner radius currently `16px` fixed hai, jabki other card radius settings dynamic hain. Isko setting-driven banaya ja sakta hai.
- QA mobile viewport par zaroor karni chahiye, especially long menu titles aur nested submenu categories ke saath.

## Conclusion

Navbar mobile drawer feature-rich aur customized hai. Standard Shopify drawer behavior ko preserve karte hue Gemora-specific visual design add kiya gaya hai. Code reusable snippets me split hai, JavaScript focus/accessibility behavior handle karta hai, aur Liquid settings ke through design customization possible hai. Overall implementation mobile-first ecommerce navigation ke liye suitable hai, bas final visual QA aur asset/icon availability check recommended hai.
