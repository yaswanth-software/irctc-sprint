# AI Feature Specification: AI Travel Assistance and Prediction System

## Problem It Solves

This AI feature addresses multiple problems documented in Part A:

- Problem 1: Tatkal Booking Crashes at 10:00 AM
- Problem 2: Search Filters Do Not Work Reliably
- Problem 6: Cancellation and Refund Information Is Difficult to Understand

Users currently struggle with confusing booking flows, poor search experiences, and lack of clarity around refunds and ticket confirmation chances.

---

## Proposed Feature — User Perspective

An AI-powered travel assistant is integrated directly into the IRCTC booking experience.

Users can type questions such as:

- “Find the fastest train to Hyderabad tomorrow”
- “Which train has the highest confirmation chance?”
- “Will my RAC ticket likely confirm?”
- “How much refund will I get if I cancel now?”

The AI assistant appears beside the train search and booking flow. It gives smart recommendations, simplified explanations, and predictive insights in real time.

---

## Model or API Choice

### Primary Model

- OpenAI GPT-4 API

### Why GPT-4

GPT-4 is chosen because:

- Strong natural language understanding
- Multilingual support
- Good reasoning ability
- Capable of simplifying railway terminology
- Handles conversational queries effectively

### Supporting ML Models

- XGBoost prediction model for ticket confirmation probability
- Historical booking analytics model for Tatkal traffic prediction

---

## Training or Input Data

### Required Data

- Historical IRCTC booking data
- Seat confirmation history
- Waitlist conversion trends
- Train schedules
- User search history
- Refund processing timelines

### Data Sources

- IRCTC internal databases
- Railway scheduling APIs
- Historical booking logs
- Cancellation datasets

### Data Availability

Most operational booking data already exists within IRCTC systems, but structured historical datasets for ML prediction may require preprocessing and cleaning.

## How Output Is Shown to the User

### Example UI Components

#### Train Search Assistant

```text
AI Recommendation:
This train has a 78% confirmation probability.
Alternative train available with faster travel time.
```

#### Refund Guidance Box

```text
Expected Refund:
₹540 will likely be refunded within 3–5 working days.
```

#### Tatkal Assistant

```text
High Traffic Warning:
Tatkal queue expected to be heavy between 10:00–10:08 AM.
Recommended to join queue early.
```

The assistant appears as:

- Floating chat panel
- Inline recommendation cards
- Smart prediction badges

---

## Confidence Threshold and Fallback

### Confidence Threshold

- AI recommendations shown only above 75% confidence

### Fallback Behavior

If confidence is low:

- System hides prediction
- Displays standard IRCTC information instead

Example:

```text
Prediction unavailable currently.
Please refer to standard booking details.
```

This prevents misleading recommendations.

---

## Success Metrics

- Reduced customer support queries
- Improved booking completion rate
- Increased user satisfaction
- Reduced cancellation confusion
- Higher search success rate

---

## Limitations and Risks

- Prediction inaccuracies during unusual travel spikes
- Bias from incomplete historical data
- Incorrect user dependence on confirmation predictions
- High infrastructure cost during peak traffic
- Multilingual understanding challenges

If predictions are wrong, users may lose trust in the platform. Therefore, predictions must always be shown with confidence indicators and disclaimers.


