# Fee Payment API Model

This repository contains a first draft of a standardized API model for handling fee payments (e.g., management fees, service charges) in the context of the OpenWealth initiative.

## Objective

The goal is to define an open, interoperable interface that allows efficient exchange of payment instructions and related information between asset managers, banks, and core banking systems.

## Structure

The model consists of the following main entities:

- **PaymentOrder**: Container object (similar to a bulk instruction)
- **AssetManager**: Information about the instructing asset manager
- **Transaction**: One or more payment transactions within the order  
  - Details  
  - Debtor  
  - Creditor  
  - Amount

## Standardization and Compatibility

The structure is being developed in alignment with existing initiatives such as the [SFTI CA Payment API](https://github.com/swissfintechinnovations/ca-payment), to ensure compatibility and identify extension opportunities.

## Contributing

This project is open for input, collaboration, and contributions from all stakeholders involved in OpenWealth and related interoperability efforts.

---

Currently maintained by Gregory Niggli for the Open Wealth Assosciation
