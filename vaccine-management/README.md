# Vaccine Tracking Smart Contract

## About
A blockchain-based smart contract system for tracking vaccine distribution, administration, and cold chain management. This contract provides a secure and transparent way to manage vaccine batches, patient vaccination records, healthcare providers, and storage facilities.

## Features

### Contract Management
- Secure contract ownership management
- Authorization controls for healthcare providers
- Role-based access control

### Vaccine Batch Management
- Register new vaccine batches with detailed information
- Track batch status and expiry dates
- Monitor storage temperatures
- Record temperature breaches
- Track available doses

### Patient Vaccination Records
- Record patient vaccinations
- Track vaccination history
- Enforce minimum intervals between doses
- Limit maximum doses per patient
- Store side effects and exemptions
- Schedule next vaccination dates

### Healthcare Provider Management
- Register authorized healthcare providers
- Track provider credentials and expiry dates
- Associate providers with healthcare facilities

### Storage Facility Management
- Register vaccine storage facilities
- Track storage capacity and current inventory
- Monitor temperature history
- Enforce temperature range requirements

## Technical Specifications

### Temperature Requirements
- Minimum Storage Temperature: -70°C
- Maximum Storage Temperature: 8°C

### Vaccination Rules
- Minimum Days Between Doses: 21 days
- Maximum Doses Per Patient: 4
- Temperature breach limit: 2 breaches before batch is marked as compromised

### Data Structures

#### Vaccine Batches
- Batch ID (32 characters)
- Manufacturer information
- Manufacturing and expiry dates
- Available doses
- Storage temperature
- Batch status
- Temperature breach count
- Storage facility location
- Additional notes

#### Patient Records
- Patient identifier
- Vaccination history (up to 10 entries)
- Completed doses count
- Side effects reports
- Vaccination exemptions

#### Healthcare Providers
- Provider address
- Role
- Facility association
- Credentials expiry date

#### Storage Facilities
- Facility ID
- Physical address
- Storage capacity
- Current inventory
- Temperature history

## Error Codes

- `ERROR-NOT-AUTHORIZED` (u100): User not authorized
- `ERROR-INVALID-BATCH` (u101): Invalid batch data
- `ERROR-BATCH-EXISTS` (u102): Batch ID already exists
- `ERROR-BATCH-NOT-FOUND` (u103): Batch not found
- `ERROR-INSUFFICIENT-VACCINE-QUANTITY` (u104): Insufficient doses
- `ERROR-INVALID-PATIENT-ID` (u105): Invalid patient identifier
- `ERROR-PATIENT-ALREADY-VACCINATED` (u106): Patient already received maximum doses
- `ERROR-TEMPERATURE-OUT-OF-RANGE` (u107): Temperature outside acceptable range
- `ERROR-VACCINE-BATCH-EXPIRED` (u108): Batch has expired
- `ERROR-INVALID-VACCINATION-LOCATION` (u109): Invalid vaccination location
- `ERROR-MAXIMUM-DOSES-REACHED` (u110): Patient has reached maximum doses
- `ERROR-MINIMUM-DOSE-INTERVAL-NOT-MET` (u111): Minimum interval between doses not met
- `ERROR-CONTRACT-OWNER-ONLY` (u112): Action restricted to contract owner

## Main Functions

### Administrative Functions
- `transfer-contract-ownership`: Transfer contract ownership
- `register-healthcare-provider`: Register new healthcare providers
- `register-storage-facility`: Register new storage facilities
- `register-vaccine-batch`: Register new vaccine batches

### Operational Functions
- `record-vaccination`: Record patient vaccination
- `update-batch-status`: Update vaccine batch status
- `record-temperature-breach`: Record temperature violations

### Read-Only Functions
- `get-vaccine-batch-info`: Retrieve batch information
- `get-patient-vaccination-record`: Retrieve patient records
- `get-storage-facility-info`: Retrieve facility information
- `is-vaccine-batch-valid`: Check batch validity
- `is-provider-authorized`: Check provider authorization
- `get-vaccine-contract-owner`: Get current contract owner

## Security Considerations

1. Only authorized healthcare providers can record vaccinations
2. Temperature breaches are permanently recorded
3. Batch validity is automatically checked before vaccination
4. Strict enforcement of dose intervals and maximum doses
5. Automatic batch status updates based on temperature breaches

## Best Practices

1. Always verify batch validity before administration
2. Regularly monitor temperature records
3. Keep provider credentials up to date
4. Monitor batch expiry dates
5. Record any side effects promptly