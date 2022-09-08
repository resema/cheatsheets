# OrderForm <!-- omit in toc -->
- [1. Overview](#1-overview)
  
# 1. Overview
- `app_order/lib/service/models/order_form.dart` -> 
- `app_order/lib/state/order_definitions.dart`
  - `func createOrder`
- `app_order/lib/widgets/order_form/...`

# Views
## Building Blocks
### Black Box

## Sequence Diagrams
### Design order
![DesignOrder](/out/diags/orderform/sd-order-old/sd-order-old.svg)

### SureSmile
![SureSmileOrder](/out/diags/orderform/sd-suresmile-old/sd-suresmile-old.svg)


### Meeting Anand
- Product launches in different countries
- OrderForm
  - not extendable in FE
- Rule Engine
  - Rule management
  - Country specific
  - [x] open/~~closed~~ to 3rd parties
    - in the futures, yes
    - or labs only offer certain combinations
  - rules not defined by business peoples (most probably)
    - product maintainer
- SAP or Google Commerce
- eCommerce Departement
  - SAP will be integrated there
  - [ ] elaborate the extension to DSCore
    - [ ] create a Gateway
  - [ ] Timeline unclear