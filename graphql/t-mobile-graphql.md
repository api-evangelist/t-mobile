# T-Mobile GraphQL Schema

## Overview

This conceptual GraphQL schema represents the T-Mobile wireless carrier platform, covering the full range of T-Mobile services including wireless accounts, device management, network connectivity, IoT (DevEdge), billing, family controls, and partner APIs. T-Mobile operates one of the largest 5G networks in the United States and provides developer access through its DevEdge IoT platform at https://developer.t-mobile.com/.

## Provider

- **Name:** T-Mobile
- **Developer Portal:** https://developer.t-mobile.com/
- **GitHub:** https://github.com/tmobile
- **Primary Services:** Wireless, 5G, IoT, DevEdge, Home Internet

## Schema Source

This schema is a conceptual representation derived from T-Mobile's public documentation, developer portal, and publicly known service offerings. It is not generated from a production GraphQL endpoint. T-Mobile's partner-facing APIs (including DevEdge IoT) require registration and are accessed via REST; this schema models the underlying domain as a GraphQL type system for exploration, integration planning, and tooling purposes.

## Type Categories

### Account & Identity
- `Account`, `TMobileAccount`, `AccountHolder`, `Subscriber`
- `APIKey`, `Token`

### Phone & Lines
- `PhoneNumber`, `Line`, `MultiSIM`

### Devices
- `Device`, `DeviceInfo`, `IMEI`, `SIM`, `eSIM`, `SIMCard`, `DeviceSIM`
- `RouterDevice`, `Hotspot`, `ConnectedCar`

### Plans & Benefits
- `Plan`, `Magenta`, `MagentaMax`, `MagentaPlus`, `FiveGPlan`
- `DataBucket`, `ShareableData`, `DataUsage`, `BingeOn`
- `TVision`, `MLBTVBenefit`, `NetflixBenefit`

### Communication
- `VoiceCall`, `CallHistory`, `SMS`, `MMS`, `Voicemail`, `GroupMessage`

### Network
- `FiveGNetwork`, `FiveGHome`, `FiveGHomeInternet`, `CoverageCheck`
- `Location`, `DeviceLocation`, `MobileEdge`
- `HomeInternet`

### Family & Controls
- `FamilyAllowance`, `FamilyControls`, `ScreenTime`, `ContentBlock`

### Billing & Payments
- `Invoice`, `BillingCycle`, `AutoPay`, `Payment`
- `DevicePayment`, `TradeIn`

### Protection & Assistance
- `DeviceProtection`, `AssuranceWireless`

### IoT & DevEdge
- `IoTConnect`, `IoTDevice`, `DevEdge`

### Rewards
- `T_LifeReward`, `Tuesday`

### Webhooks
- `Webhook`

## Queries

- `account(id: ID!)` — Fetch a T-Mobile account by ID
- `subscriber(msisdn: String!)` — Fetch subscriber by phone number
- `device(imei: String!)` — Look up a device by IMEI
- `coverageCheck(lat: Float!, lng: Float!)` — Query 5G/LTE coverage at a location
- `invoice(id: ID!)` — Retrieve a billing invoice
- `iotDevice(deviceId: ID!)` — Retrieve an IoT device record (DevEdge)
- `callHistory(lineId: ID!, limit: Int)` — Recent call records for a line
- `rewards(accountId: ID!)` — T-Life rewards and Tuesday offers

## Mutations

- `activateSIM(simId: ID!, lineId: ID!)` — Activate a SIM card on a line
- `updatePlan(accountId: ID!, planId: ID!)` — Change the plan on an account
- `addLine(accountId: ID!, deviceId: ID!)` — Add a new wireless line
- `setFamilyControls(lineId: ID!, controls: FamilyControlsInput!)` — Configure family controls
- `makePayment(accountId: ID!, amount: Float!, method: String!)` — Submit a payment
- `registerWebhook(url: String!, events: [String!]!)` — Register a webhook endpoint
- `addIoTDevice(deviceInput: IoTDeviceInput!)` — Register an IoT device on DevEdge

## References

- T-Mobile Developer Portal: https://developer.t-mobile.com/
- T-Mobile GitHub: https://github.com/tmobile
- T-Mobile IoT: https://www.t-mobile.com/business/iot
- T-Mobile Business: https://www.t-mobile.com/business
- T-Mobile Investors: https://investor.t-mobile.com/
