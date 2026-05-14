# IRCTC Feature Specifications — Part B

---

# Feature Spec 1: Tatkal Smart Queue System

## Problem Statement

As documented in Part A, Tatkal booking on IRCTC becomes unstable during peak hours around 10:00 AM. Users experience crashes, session timeouts, failed payments, and unclear error handling. Millions of daily users including emergency travelers and office workers are affected.

## Current State (from Part A)

In the current Tatkal booking flow, the system fails between booking confirmation and payment processing during peak load. Users repeatedly refresh pages without understanding queue position or server status. The platform provides no transparency during traffic spikes.

## Proposed Solution

Introduce a virtual smart queue system for Tatkal booking. Instead of allowing all users to hit booking APIs simultaneously, users are automatically placed into a live queue with real-time status updates, estimated waiting time, and automatic progression into booking.

## Proposed User Flow — Step by Step

1. User opens IRCTC before Tatkal opening time.
2. User selects train and Tatkal quota.
3. At 10:00 AM, system automatically assigns queue number.
4. User sees estimated waiting time.
5. Queue status updates live every few seconds.
6. User automatically enters booking page when slot becomes available.
7. Passenger details auto-load from saved profiles.
8. Payment page opens smoothly without reload loops.
9. User receives confirmation message.

## Technical Implementation Plan

### System components affected

- Booking server
- Session management
- Payment gateway integration
- Queue management service
- Notification system

### New data requirements

- Queue token ID
- Queue timestamp
- Estimated wait duration
- User booking priority status

### API changes

- New queue assignment API
- Queue status polling endpoint
- Queue completion callback API

### Frontend changes

- Queue progress screen
- Live status indicator
- Retry prevention state handling
- Auto-refresh booking transition

### Third-party services (if any)

- Redis for queue caching
- SMS notification integration

## Success Metrics

- Reduce Tatkal booking failures by 50%
- Reduce manual page refreshes
- Improve successful payment completion rate
- Reduce support complaints during Tatkal hours

## Edge Cases and Constraints

- Queue service overload
- Payment timeout during queue transition
- Government booking infrastructure limitations
- Graceful fallback to waitlist if queue fails

---

# Feature Spec 2: Persistent Smart Filters

## Problem Statement

Part A identified that IRCTC search filters do not reliably update train results and reset during navigation. Users repeatedly lose filter state and must manually reapply preferences.

## Current State (from Part A)

Users apply filters such as Sleeper class or Available Seats Only, but results remain inconsistent. When navigating back from train details, filters disappear and search context resets.

## Proposed Solution

Create persistent smart filters that remain active across navigation and update results instantly. Users can save preferred filter combinations for future searches.

## Proposed User Flow — Step by Step

1. User searches trains.
2. User applies desired filters.
3. Results instantly refresh with applied filters.
4. Selected filters appear as removable filter chips.
5. User opens train details.
6. User returns to search results.
7. Previously selected filters remain active.
8. User optionally saves filter preset.

## Technical Implementation Plan

### System components affected

- Search engine
- Filter service
- Frontend state management

### New data requirements

- Saved filter preferences
- Search session state

### API changes

- Persistent filter API
- Saved preference API

### Frontend changes

- Dynamic filter chips
- Persistent state handling
- Real-time filtering updates

### Third-party services (if any)

- None

## Success Metrics

- Reduce repeated filter applications
- Improve search completion speed
- Reduce navigation frustration

## Edge Cases and Constraints

- Slow network synchronization
- Filter conflicts
- Cached stale search data

---

# Feature Spec 3: Auto-Save Seat Preference System

## Problem Statement

Part A documented that berth preferences often reset during booking flow, especially on mobile browsers. This affects senior citizens, families, and overnight travelers.

## Current State (from Part A)

Users select berth preferences but selections disappear after moving between booking stages. Users receive no confirmation that preference was saved.

## Proposed Solution

Implement real-time auto-save for berth preferences with visible confirmation indicators and session persistence.

## Proposed User Flow — Step by Step

1. User selects train.
2. User chooses berth preference.
3. System instantly auto-saves preference.
4. Save confirmation message appears.
5. User continues booking.
6. Preference remains visible throughout flow.
7. Final review screen confirms saved preference.

## Technical Implementation Plan

### System components affected

- Booking flow service
- Session storage
- Passenger preference database

### New data requirements

- Temporary berth preference state
- Save timestamp

### API changes

- Preference auto-save endpoint
- Session restore API

### Frontend changes

- Auto-save indicator
- Persistent selection state
- Error retry prompts

### Third-party services (if any)

- None

## Success Metrics

- Reduce seat preference resets
- Improve booking completion confidence
- Reduce repeated passenger edits

## Edge Cases and Constraints

- Session expiry
- Mobile browser refresh
- Multiple passenger conflicts

---

# Feature Spec 4: Multi-Step Passenger Form

## Problem Statement

Part A identified that the passenger details form is overcrowded and difficult to scan. Users struggle to identify mandatory fields and complete booking quickly.

## Current State (from Part A)

Passenger information, insurance, berth preferences, GST details, and CAPTCHA appear together on one overloaded screen. Validation errors force users to scroll repeatedly.

## Proposed Solution

Break the passenger form into smaller guided steps with progress indicators and grouped information sections.

## Proposed User Flow — Step by Step

1. User opens booking form.
2. Step 1 collects passenger details.
3. Step 2 collects berth preferences.
4. Step 3 handles optional services.
5. Step 4 shows payment preview.
6. Progress bar indicates completion status.
7. Validation occurs instantly within each section.
8. User completes booking faster.

## Technical Implementation Plan

### System components affected

- Booking frontend
- Validation engine
- Session state management

### New data requirements

- Multi-step completion state
- Partial form save status

### API changes

- Step validation endpoint
- Partial save API

### Frontend changes

- Multi-step wizard
- Progress tracker
- Inline validation

### Third-party services (if any)

- None

## Success Metrics

- Reduce form abandonment rate
- Reduce booking errors
- Improve mobile usability

## Edge Cases and Constraints

- Session interruption
- Incomplete form recovery
- CAPTCHA timeout

---

# Feature Spec 5: Responsive Mobile Redesign

## Problem Statement

Part A identified severe mobile usability problems including overlapping menus, broken layouts, and horizontal scrolling.

## Current State (from Part A)

The mobile website behaves inconsistently across screen sizes. Important buttons become inaccessible and layouts shift unpredictably.

## Proposed Solution

Redesign the IRCTC mobile web experience using responsive layouts optimized for smaller screens and touch interactions.

## Proposed User Flow — Step by Step

1. User opens IRCTC mobile website.
2. Homepage loads optimized mobile layout.
3. Navigation menu opens cleanly.
4. Search forms resize correctly.
5. Booking buttons remain accessible.
6. Sticky elements avoid overlapping content.
7. User completes booking without zooming.

## Technical Implementation Plan

### System components affected

- Mobile frontend
- CSS layout engine
- Responsive design framework

### New data requirements

- Device layout preferences

### API changes

- None

### Frontend changes

- Responsive navigation
- Mobile-friendly buttons
- Adaptive layouts
- Optimized typography

### Third-party services (if any)

- Responsive UI framework

## Success Metrics

- Reduce mobile bounce rate
- Increase mobile booking completion
- Reduce accidental clicks

## Edge Cases and Constraints

- Older Android browsers
- Slow mobile internet
- Small-screen compatibility

---

# Feature Spec 6: Refund Transparency Dashboard

## Problem Statement

Part A documented that cancellation, refund, and TDR flows are confusing and difficult to understand. Users lack transparency regarding refund amounts and timelines.

## Current State (from Part A)

Refund details are spread across multiple pages with technical terminology and poor guidance. Users repeatedly check refund status manually.

## Proposed Solution

Introduce a refund transparency dashboard showing cancellation charges, refund status, timelines, and TDR guidance in one place.

## Proposed User Flow — Step by Step

1. User opens booked ticket history.
2. User clicks cancellation details.
3. Dashboard shows expected refund amount instantly.
4. Refund timeline appears visually.
5. TDR eligibility guidance is displayed.
6. User receives status updates automatically.
7. Refund completion notification is sent.

## Technical Implementation Plan

### System components affected

- Refund management system
- TDR service
- Notification service

### New data requirements

- Refund processing timestamps
- Refund stage tracking
- TDR eligibility flags

### API changes

- Refund tracking API
- TDR explanation endpoint

### Frontend changes

- Refund dashboard
- Timeline UI
- Status tracker

### Third-party services (if any)

- SMS/email notification service

## Success Metrics

- Reduce refund-related support requests
- Improve cancellation confidence
- Increase refund status transparency

## Edge Cases and Constraints

- Delayed bank processing
- Partial refunds
- TDR disputes
- Payment gateway failures

---