# Hybrid Model Approaches

## Situation

![Hybrid Model](../diags/byte+/cv-byte%2B.drawio.svg)

The diagram shows a simplification of the current situation for DP&S and Byte. 

The goal is the achieve a hybrid model of Byte+ integrated in DP&S.

---
## Complication
Regarding the existing solution of Byte a hybrid model Byte+ should close the gap between Byte and SureSmile. But without loosing speed in the market.

Certain parts of Byte such as treatment planning for Byte could be synchronised with Aligner, SureSmile and others in DS Core.

The two current solutions have some parts which are very similar:
- Dashboard
- Notification center
- Treatment steps
- Media Library

In other regions Byte has concepts, which are missing or only planned in DSCore:
- Treatment planning
- PMS integration via NexHealth
- Mobile application

And there is also concepts or integrations, which are an extension of what Byte is offering:
- Practice stuff onboarding
- Laboritories onboarding
- Device handling 

---
## Questions
### Q1: What are possible approaches?

---
## Answers
### Q1: 2 different Options are possible

### Option 1:
- [ ] keeping the backend and transition to Flutter frontend
  - [ ] use Flutter's GraphQL library
  - [ ] integrate treatment planning into DSCore
    - [ ] use procedures/step service/notification/storage/media library/others
  - [ ] map data models
    - [ ] define converter
  
### Option 2:
- [ ] keeping react app and extend backend to cover all Byte logic
  - [ ] adjust communication between FE and BE
  - [ ] integrate NexHealth
  - [ ] integrate Shopify
  - [ ] and much more

---
## Conclusion
