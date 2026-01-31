# ⚡ Community EV Charging Load Balancer — UI Flow

This document explains the end-to-end user interface flow for the Community EV Charging Load Balancer platform.  
It covers how drivers, fleets, grid operators, and admins interact with the system and how UI actions connect to backend services and Smartcar-based vehicle integrations.

---

## 🎯 Goals of the UI

- Fair charger access for everyone
- Grid-safe power management
- Verified emergency handling
- Transparent scheduling decisions
- Abuse prevention
- Real-time updates
- Simple experience for drivers

---

# 👤 User Roles

- Public EV Drivers
- Fleet Operators / Enterprises
- Grid / Utility Operators
- Platform Admins

---

# 🧑‍🚗 Driver UI Flow

---

## 1. Home Screen

Displays:

- Battery percentage
- Estimated range
- Current location map
- Nearby charging stations
- Grid congestion badge (Green / Yellow / Red)
- Buttons:
  - Request Charging Slot
  - Emergency / Low Battery

---

## 2. Connect Vehicle (First-Time Users)

Prompt:

> Connect your vehicle account to enable smart scheduling.

Action:

- Connect via Smartcar
- Redirect to OEM login
- User grants permissions
- Redirect back
- Vehicle linked successfully

Backend:

- OAuth tokens stored securely
- Vehicle IDs synced

---

## 3. Charger Selection

Shows:

- Charger distance
- Connector type
- Max power
- Estimated wait time
- Available window
- Price estimate
- Grid load note

CTA:

- Request Slot

---

## 4. Slot Allocation Result

Backend applies:

- Grid capacity rules
- Fairness engine
- Emergency classifier
- Fleet quotas
- Dynamic pricing

Displays:

- Start time
- End time
- Power limit
- Cost estimate
- Reason label:

Examples:

- Scheduled later due to peak demand
- Priority granted — battery critically low

---

## 5. Emergency Request Flow

Trigger:

- Emergency / Low Battery button

Steps:

1. Warning about misuse penalties
2. Reason selection:
   - Battery critically low
   - Medical
   - Unsafe area
3. Telemetry verification in progress

Result:

- Emergency approved → priority slot
- Not approved → normal queue

Abuse attempts are logged.

---

## 6. Charging Session Screen

Displays:

- Current battery %
- kWh delivered
- Time remaining
- Power throttling indicator
- Grid stability message

Updates in real time via WebSockets.

---

# 🚛 Fleet Operator UI Flow

---

## 1. Fleet Dashboard

Shows:

- Total vehicles
- Charging now
- Waiting
- Emergency flags
- Average wait time
- Daily energy usage

---

## 2. Vehicle Detail View

Shows:

- Vehicle ID / VIN
- Location
- Battery %
- Assigned charger
- Slot time
- Trip urgency

CTA:

- Request Priority (logged and audited)

---

## 3. Fleet Emergency Request

Requires:

- Service type
- Trip justification
- Route ID

System:

- Enforces fleet quotas
- Logs audit records
- Verifies vehicle telemetry

---

# ⚡ Grid / Utility Operator UI Flow

---

## 1. Cluster Map View

Displays:

- Transformer utilization %
- Charger clusters
- Active sessions
- Throttled chargers
- Queue length

---

## 2. Peak Control Panel

Controls:

- Cluster load caps
- Emergency quota %
- Fleet quota %
- Dynamic pricing multipliers

---

## 3. Alerts Center

Shows:

- Overload risk alerts
- Telemetry dropouts
- Emergency spikes
- Abuse pattern detection

---

# 🏢 Enterprise Onboarding Flow

---

## Signup Steps

1. Company profile
2. Legal documents upload
3. Vehicle registry
4. API integration option
5. Compliance agreement

Status:

- Pending
- Approved
- Rejected

---

# 🛡️ Admin & Audit UI

---

## Verification Panel

- Approve or reject fleet applications
- Review emergency abuse
- Suspend vehicles or accounts
- Manual override controls

---

## Fairness Analytics

Shows:

- Wait time by category
- Emergency approvals vs rejections
- Peak load reduction
- Grid incidents avoided

---

# 🔌 Realtime UX Infrastructure

- REST APIs for actions
- WebSockets for:
  - Charger availability
  - Charging status
  - Slot changes
  - Grid alerts

---

# 🚫 What the UI Never Shows

- OAuth tokens
- Internal priority scores
- ML weights
- Transformer raw telemetry
- Security credentials

---

# 🧠 Why This Flow Works

- Uses real OEM integrations via Smartcar OAuth
- Prevents fake emergency claims
- Maintains fairness
- Protects grid stability
- Supports fleets and utilities
- Provides transparency to users

---

