# Impact vs Effort Matrix

---

# The Matrix

|                   | Low Effort | High Effort |
|-------------------|------------|--------------|
| **High Impact**   | Persistent Smart Filters, Auto-Save Seat Preference, Multi-Step Passenger Form | Tatkal Smart Queue System, Responsive Mobile Redesign |
| **Low Impact**    | Refund Transparency Dashboard | AI Travel Assistance and Prediction System |

---

# How I Scored Each Dimension

## Impact Scoring (1–5)

Impact was scored based on:

- Number of affected users
- Whether the issue affects the core booking flow
- Frequency of occurrence
- Severity of user frustration
- Effect on booking success rate

---

## Effort Scoring (1–5)

Effort was scored based on:

- Number of backend systems affected
- Infrastructure requirements
- UI redesign complexity
- API dependency risks
- Railway system integration complexity

---

# Placement Justifications

## Tatkal Smart Queue System — High Impact / High Effort

Tatkal booking failures affect millions of users daily during peak booking hours. The solution requires major backend infrastructure changes including queue management, load balancing, and session coordination. This feature should be prioritized because it solves one of the most visible IRCTC pain points.

---

## Persistent Smart Filters — High Impact / Low Effort

Search filtering problems affect almost every user searching trains. The feature mainly requires frontend state persistence and moderate API updates without major infrastructure changes. This makes it a quick-win usability improvement.

---

## Auto-Save Seat Preference — High Impact / Low Effort

Seat preference resets directly affect booking confidence for families and senior citizens. The implementation mainly involves frontend state persistence and lightweight backend session storage. It provides strong user trust improvements with relatively low engineering effort.

---

## Multi-Step Passenger Form — High Impact / Low Effort

The overloaded passenger form impacts every booking flow, especially on mobile devices. The solution primarily involves frontend restructuring and validation improvements rather than deep backend modifications. This makes it a highly valuable usability upgrade with manageable implementation effort.

---

## Responsive Mobile Redesign — High Impact / High Effort

A large percentage of IRCTC users access the platform through mobile browsers. Fully redesigning mobile responsiveness requires extensive frontend rebuilding, testing across devices, and layout optimization. Despite high effort, the impact justifies prioritization.

---

## Refund Transparency Dashboard — Low Impact / Low Effort

Refund confusion affects cancellation-related flows rather than the primary booking flow. The implementation is comparatively simple because it mostly reorganizes existing information into a cleaner dashboard. It improves trust but has lower overall impact compared to booking-related issues.

---

## AI Travel Assistance and Prediction System — Low Impact / High Effort

The AI assistant can improve user understanding and prediction accuracy, but it requires large datasets, ML infrastructure, and ongoing model maintenance. Since the platform's core usability problems should be fixed first, this feature is lower priority despite innovation potential.

---

# Recommended Sprint Order

1. Persistent Smart Filters — Quick usability improvement with low engineering effort.
2. Auto-Save Seat Preference — Improves booking trust and reduces frustration.
3. Multi-Step Passenger Form — Simplifies core booking flow.
4. Refund Transparency Dashboard — Improves post-booking clarity.
5. Tatkal Smart Queue System — Major infrastructure upgrade for peak traffic handling.
6. Responsive Mobile Redesign — Large-scale frontend modernization.
7. AI Travel Assistance and Prediction System — Advanced enhancement after core flows stabilize.

---