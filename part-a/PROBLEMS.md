# IRCTC Problem Discovery — Part A

## Summary

- Total problems documented: 6
- Platform explored: irctc.co.in
- Devices used:
  - Desktop Chrome
  - Mobile Chrome

---

# Problem 1: Tatkal Booking Crashes at 10:00 AM [Given]

## What is broken

During Tatkal booking hours, especially around 10:00 AM, the IRCTC platform becomes unstable. Pages freeze, sessions expire, payment pages fail to load, and users receive unclear errors or no feedback.

The system does not provide queue visibility or meaningful status updates during peak booking traffic.

## Affected users

- Daily commuters
- Emergency travelers
- Students
- Office workers
- Travel agents
- Users with slow internet connections

Millions of users attempt Tatkal booking daily.

## Frequency

Occurs every day during Tatkal booking hours.

Highest traffic and failures are observed between 9:58 AM and 10:10 AM.

## Current flow — step by step

1. User opens IRCTC around 9:50 AM.
2. User logs into account.
3. User searches for train and selects Tatkal quota.
4. User waits for booking opening time.
5. At 10:00 AM user clicks “Book Now.”
6. Website becomes slow or unresponsive.
7. CAPTCHA reloads or session refreshes unexpectedly.
8. Passenger details page partially loads or crashes.
9. Payment page times out.
10. User refreshes page repeatedly.
11. Tatkal tickets become unavailable.
12. User receives waitlist or “Not Available” status.

## Where exactly it breaks

Failure mainly occurs between Step 5 and Step 9.

The booking infrastructure fails to handle high simultaneous traffic, causing session timeouts and booking interruptions.

---

# Problem 2: Search Filters Do Not Work Reliably [Given]

## What is broken

Train search filters such as Sleeper class, Available seats only, and departure timing do not consistently update results.

Filters also reset after page refresh or browser back navigation.

## Affected users

- First-time users
- Elderly passengers
- Mobile users
- Long-distance travelers
- Users comparing multiple trains

## Frequency

Occurs frequently during train searches across multiple routes.

## Current flow — step by step

1. User opens train search page.
2. User enters source and destination stations.
3. User selects travel date.
4. User clicks “Search.”
5. Train list loads.
6. User applies “Sleeper” filter.
7. Some non-sleeper trains still remain visible.
8. User applies “Available seats only.”
9. Unavailable trains continue appearing.
10. User opens train details.
11. User clicks browser back button.
12. Previously selected filters disappear.
13. User must apply filters again.

## Where exactly it breaks

Failure occurs between Step 6 and Step 12.

Frontend filters are not reliably synchronized with search result rendering and navigation state.

## Screenshot or description

Screenshot saved in:
assets/screenshots/filter-issue.png

---

# Problem 3: Seat Selection Resets During Booking [Given]

## What is broken

Selected berth preferences or seat choices are not consistently preserved during the booking process.

The issue is more common on mobile browsers.

## Affected users

- Senior citizens
- Women travelers
- Families
- Mobile users
- Overnight travelers

## Frequency

Occurs frequently during booking flow testing, especially on mobile devices.

## Current flow — step by step

1. User searches for train.
2. User selects train and travel class.
3. User proceeds to booking page.
4. User selects berth preference such as “Lower Berth.”
5. User clicks Proceed.
6. Passenger details page opens.
7. Earlier berth preference is missing or reset.
8. User returns to previous page.
9. Previous selection is lost.
10. User repeats the process.
11. Booking continues without confirmation of preference saving.

## Where exactly it breaks

Failure occurs between Step 4 and Step 7.

Seat preference data is not reliably persisted between booking stages.

---

# Problem 4: Passenger Details Form Is Overloaded and Confusing [Self-Discovered]

## How I found it

While testing the booking flow on desktop and mobile, I proceeded from train selection to passenger information entry.

## Screenshot or description

The passenger details page contains:
- Passenger information
- Berth preference
- Insurance option
- Auto-upgrade checkbox
- GST fields
- Meal preference
- CAPTCHA
- Contact details

All sections are displayed together with poor visual separation.

## What is broken

The passenger form is overcrowded and difficult to scan quickly.

Important actions and optional settings are visually mixed together, increasing user confusion.

## Affected users

- First-time users
- Elderly users
- Mobile users
- Users booking under time pressure
- Users with low digital literacy

## Frequency

Occurs during every booking flow.

## Current flow — step by step

1. User selects train and quota.
2. User clicks “Book Now.”
3. Passenger details page opens.
4. User sees multiple sections and checkboxes together.
5. User scrolls repeatedly to locate mandatory fields.
6. User enters passenger information.
7. CAPTCHA section appears near bottom.
8. User misses mandatory field or option.
9. Validation error appears after submit.
10. User scrolls back searching for missing information.
11. Booking process becomes slower.

## Where exactly it breaks

Failure occurs between Step 4 and Step 9.

The form lacks proper hierarchy and separation between mandatory and optional fields.

## Screenshot or description

Screenshot saved in:
assets/screenshots/passenger-form.png

---

# Problem 5: Mobile Website Navigation Breaks Frequently [Self-Discovered]

## How I found it

I tested the IRCTC website using a mobile browser and explored login, search, and booking flows.

## Screenshot or description

Observed issues:
- Overlapping menus
- Small buttons
- Horizontal scrolling
- Layout shifts during loading
- Sticky elements blocking actions

## What is broken

The mobile web experience is inconsistent and difficult to navigate.

UI elements resize unpredictably and important buttons become difficult to access.

## Affected users

- Mobile-only users
- Rural users
- Elderly users
- Users with small-screen devices

## Frequency

Observed repeatedly across multiple pages during testing.

## Current flow — step by step

1. User opens IRCTC on mobile browser.
2. Homepage loads slowly.
3. User opens navigation menu.
4. Menu overlaps page content.
5. User searches for train.
6. Results load with compressed layout.
7. User attempts to click booking button.
8. Wrong element gets tapped accidentally.
9. Horizontal scrolling appears unexpectedly.
10. Sticky footer blocks important buttons.
11. User refreshes page or zooms out.

## Where exactly it breaks

Failure occurs between Step 4 and Step 10.

Responsive layout behavior is inconsistent across different screen sizes.

---

# Problem 6: Cancellation and Refund Information Is Difficult to Understand [Self-Discovered]

## How I found it

I explored ticket cancellation and refund-related pages after checking booked ticket history.

## Screenshot or description

Refund information is spread across:
- cancellation confirmation page
- refund rules page
- TDR information pages
- policy links

Important information is hidden inside dense text blocks.

## What is broken

Users cannot clearly understand:
- refund amount
- refund timing
- cancellation charges
- TDR eligibility
- refund status

The flow lacks transparency and clear explanations.

## Affected users

- First-time travelers
- Elderly users
- Users cancelling urgent tickets
- Users filing TDR claims

## Frequency

Occurs during every cancellation-related interaction.

## Current flow — step by step

1. User opens booked ticket history.
2. User selects booked ticket.
3. User clicks “Cancel Ticket.”
4. Confirmation popup appears.
5. Refund deduction details remain unclear.
6. User searches for refund policy.
7. User navigates through multiple pages.
8. Technical terms like “TDR” appear without explanation.
9. User completes cancellation without confidence about refund amount.
10. User repeatedly checks refund status through SMS or email.

## Where exactly it breaks

Failure occurs between Step 5 and Step 9.

The cancellation flow lacks transparent communication and contextual guidance.

---