# DHCP: Your Network's Address Distributor

## What is DHCP?
Dynamic Host Configuration Protocol (DHCP) automatically assigns network configuration to devices.

## Key Function
- Assigns IP addresses
- Provides subnet masks
- Configures network gateways

## Real-World Analogy
Like a phone carrier giving out phone numbers:
- Temporary assignment
- Can be renewed
- Manages address distribution

## DHCP Process: Four-Step Dance

### 1. DHCP Discover
- Device broadcasts: "I need an IP address!"
- Searches for DHCP server

### 2. DHCP Offer
- Server responds with:
    - IP address
    - Lease time
    - Subnet mask
    - Other network details

### 3. DHCP Request
- Device accepts offer
- Broadcasts acceptance to all servers

### 4. DHCP Acknowledgement
- Server confirms assignment
- Connection established

## Benefits
- Automatic IP address management
- Prevents duplicate addresses
- Simplifies network administration

## Typical Setup
- Home networks: Router acts as DHCP server
- Large networks: Dedicated DHCP server