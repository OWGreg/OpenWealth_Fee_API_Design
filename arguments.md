# Why banks should implement the future OW Fee API

The OpenWealth (OW) Fee API is a proposed standard to digitize and streamline the exchange of fee instructions between external asset managers (EAMs) and custodian banks. It builds upon existing Swiss API standards, particularly the SFTI Payment API, and aligns with the modular OpenWealth API framework.

This document outlines key reasons why banks, especially those already engaged with OpenWealth, should implement the Fee API.

## 1. Alignment with SFTI Payment API

- The Fee API adopts a structure and logic similar to the widely implemented SFTI Payment API.
- Banks can leverage existing infrastructure such as authentication mechanisms, data models, and validation logic.
- The incremental effort to implement the Fee API is therefore minimal.

## 2. Structured and auditable fee instruction handling

- The API replaces manual, error-prone processes based on Excel, email, or PDF.
- It ensures consistent, transparent, and traceable handling of fee instructions.
- This approach supports internal control requirements, audit readiness, and regulatory compliance.

## 3. Clear separation from standard payment orders

- Although similar in mechanics, fee instructions are conceptually distinct from traditional payments.
- The API supports precise categorization of instructions as fees, improving processing and reporting accuracy.
- This distinction is beneficial for financial, compliance, and operational purposes.

## 4. Seamless integration into the OpenWealth ecosystem

- The Fee API complements existing OpenWealth APIs for onboarding, portfolio data, and transactions.
- It simplifies third-party integrations with portfolio management systems and external asset manager tools.
- Banks strengthen their digital offering and positioning by adopting this additional standard.

## 5. Scalable and automatable fee processing

- Enables straight-through processing of both recurring and one-time fees.
- Reduces manual handling and operational risk, improving turnaround times and reliability.
- The design is extensible and can support features such as approval workflows or transaction monitoring.

## 6. Elimination of fragmented or proprietary solutions

- In the absence of a standard, banks and EAMs resort to individual file formats and custom workflows.
- These are difficult to scale, maintain, or audit.
- The Fee API introduces a uniform, maintainable, and future-proof approach.

## 7. Increased return on existing OpenWealth investments

- Banks that have already adopted OpenWealth APIs can integrate the Fee API with minimal additional investment.
- This maximizes the value of their current API infrastructure.
- It contributes to the overall maturity and consistency of OpenWealth-based interfaces.

---

The OW Fee API offers a practical, compliant, and scalable solution for fee-related interactions between banks and EAMs. Its compatibility with the Payment API and consistency with the OpenWealth model make it a low-effort, high-impact enhancement to a bank’s digital service portfolio.
