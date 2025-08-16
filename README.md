#  OpenChargeMap API Testing

This repository contains API test scripts for two endpoints:
1. **Get POIs**
2. **Get Reference Data**

---

## 📂 Contents
- **`collections/OpenChargeMap_collection.json`** — Postman collection containing requests and test scripts.
- **`collections/production_environment.json`** — Postman environment file with test variables.
- **`report/TestReport.html`** — HTML execution report generated via Newman.
- **`README.md`** — Instructions, observations, and assumptions.

---

## 🛠 Instructions: How to Import and Run the Tests

### 1. Import Postman Files
1. Open **Postman**.
2. Click **Import** → select:
   - `OpenChargeMap_collection.json`
   - `production_environment.json`

### 2. Configure Environment Variables
In the imported environment:
- `baseUrl` — API base URL.
- `apiKey` — API key

Default values are already added for above variables, if needed they can be updated.

### 3. Run Tests in Postman
1. Select the imported environment from the **environment dropdown**.
2. Open the **OpenChargeMap_collection**.
3. Click **Run** to execute all requests.

### 4. Observations
Get POIs endpoint:
- status code is always 200
- Response time occasionally exceeded the 1000ms threshold
- Schema is matched with expected structure
- When maxresults=5 , exactly 5 results are returned
- All returned POIs are with in 10km of the specified coordinates 

Get Reference endpoint:
- status code is always 200
- Response time is under 1000ms threshold
- Schema is matched with expected structure
- ChargerTypes array contains both "Fast" and "Slow" chargers
- All StatusTypes have unique IDs

### 5. Assumptions
- In Get POI endpoint : For checking POIs within 10 km, the test uses `AddressInfo.Distance` from the API response, assuming it is the distance from specified coordinates.
  
