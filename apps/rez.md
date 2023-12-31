---
permalink: /apps/rez
layout: post
categories: Android
title: ReZ Launcher
---

[![Get it on Google Play](https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png){: height="60"}](https://play.google.com/store/apps/details?id=com.perryoncrack.rez&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1)

## Development Status

- In-development
    - Experimental features to address some gesture navigation issues

- Planned features
    - On-coming calendar events on top panel
    - Update scribble settings screens & backend
    - More notification style in app info menu
    - App list scrollbar (waiting for the official Jetpack Compose implementation)

- "No promise but I will look into them" features
    - Double tap to lock screen
    - Option to hide status bar
    - Foldable device screen layout
    - Pinned shortcut/PWA
    - Customizable font

- Known issues
    - Unable to use Samsung OneUI's gesture navigation
    - Crash when moving or resizing widgets on some devices

---

## Changelogs

### Version 1.8.1-fix1 (2023-12-31)

- Bug Fixes:
    - Re-added SET_ALARM permission because some device manufactures' clock apps need it to view alarms.

### Version 1.8.1 (2023-12-28)

- New Features:
    - Notification dot color is now customizable.
    - Clicking the date of home screen clock now opens the calendar.

- Bug Fixes:
    - Fixed some UI elements using the incorrect color & size.
    - Removed unnecessary permissions.

### Version 1.8-fix1 (2023-12-22)

- Bug Fixes:
    - Fixed an issue where some Android 14 devices can't add widgets that require configuration.

### Version 1.8 (2023-12-21)

- New Features:
    - Work profile support:
        - Supported features:
            - Work apps: Show in app list, suggestions & search, hidden when work profile is paused.
            - Work app widgets: Show in widget list, hidden when work profile is paused.
            - Notification dot for work apps
        - Unsupported features (due to API constraints):
            - Media control for work apps
            - Contact search for work profile contacts
    - Customization Options: (Access them in `Settings -> Customizations`)
        - Icon pack support
        - UI color adjustment
        - Smaller icon size options

- Changes:
    - Wallpaper option in Settings has been moved into Customizations menu.

- Bug Fixes:
    - Various stability fixes.

### Version 1.7 (2023-12-11):

- New Features:
    - Contact search:
        - You can access its settings under `Settings -> Contact Search`.
    - App &amp; contact alias:
        - You can access it in apps/contacts' info menu(long press menu).

- Changes:
    - Scribble search now queries against words in app/contact's name.
    - Updated user manual, now with GIFs! *(They are animated webp actually.)*

- Bug Fixes:
    - Fixed an issue where scribble with pointer devices other than touch causing unexpected behaviors and crashing.
    - Various stability fixes.

### Version 1.6-fix3 (2023-11-21):

- Bug Fixes
    - Fixed an issue where notification dot will crash the launcher in some condition.

### Version 1.6-fix2 (2023-11-19):

- Bug Fixes
    - Fixed various app crashing problems (hopefully), these include:
        - Crash when widget list failed to fetch app names.
        - Crash when failed to launch an app or its app info's activity.
        - Crash when using the app visibility button popup.
        - Crash when opening up this launcher.
    - Fixed launching app shortcut didn't get counted to usage.

### Version 1.6-fix1 (2023-11-16):

- Bug Fixes
    - Fixed app info menu not closing after opening an app shortcut.

### Version 1.6 (2023-11-06)

- New Features
    - Widget support:
        - Swipe to the left or right in Home Screen to access the new widget space.
        - You can access widget related settings under `Settings -> Widget`.

- Bug Fixes
    - App List now fills up the screen properly on wide screen devices.

### Version 1.5-fix1 (2023-10-20)

- Bug Fixes:
    - Fixed an issue where some notifications can crash the launcher.
    - Fixed faulty home button detection implementation.

### Version 1.5 (2023-10-17)

- New Features:
    - Media Control in the top panel. (Enable this feature in `Settings -> Media Control`)
    - More fine-grained app hiding, see `Settings -> User Manual -> Hiding App` for more detail.

- Changes:
    - Quick Launch area will now show an arrow when it's empty.

- Bug Fixes:
    - Fixed an issue where notification dot not being updated properly.

- New Bugs:
    - In the top panel, right after swiping, clicks will sometimes only response after a few more clicks.

### Version 1.4 (2023-09-27)

- New Features:
    - Update changelog dialog
    - Notification dot & app notification in app info menu (Enable them in "Settings" -> "Notification Dot")
    - Hiding apps from suggestions
    - Improved onboarding experience
    - Added Korean handwriting support

- Changes:
    - Quick Launch Area's icons will now adjust their position base on the icon amount.

### Version 1.3 (2023-09-16)

- New Features:
    - Analog clock.

- Improvements:
    - Handwriting should be more responsive on mid-end & low-end devices.
    - More adaptive screen layout, UI elements won't get covered on shorter screen anymore.
    - Backend algorithm improvement, app searching should be much faster and less resource intensive.

### Version 1.2-fix1 (2023-08-12)

- Fixed a usage collection issue.

### Version 1.2 (2023-08-11)

- Rewrote suggestion algorithm.
- Redesigned app info menu.
- Added access to app shortcuts.
- Thicken the font for better visibility.
- Fixed navigation, status bar and other icons not display correctly when system is using light mode.

### Version 1.1-fix1 (2023-08-06)

- Fixing the crashing issue.

### Version 1.1 (2023-07-29)

- Fixed some layout issues.
- Attempted to fix the crashing issue.

### Version 1.0 (2023-07-14)

- Initial release.

---

- [Privacy Policy](/legal/rez/privacy.html)
- [Terms & Conditions](/legal/rez/terms.html)

{% include ko-fi-button.html %}
