# Cryptocurrency Data API

This API provides endpoints to fetch cryptocurrency data and calculate price deviations.

Deployed on AWS EC2: [AWS: http://3.25.95.38/api/stats?coin=bitcoin](http://3.25.95.38/api/stats?coin=bitcoin)

**Postman Documentation:** [Cryptocurrency Data API Documentation](https://dark-satellite-379351.postman.co/workspace/7d3d576c-5a1b-4446-9ea2-450401b4ed21/documentation/31555061-9675d3a2-2ad5-4424-9ee8-84cf320e896b)

## Base URL

```
http://localhost:7000/api
```
- Or:
```
http://3.25.95.38/api
```

## Endpoints

### 1. Get Cryptocurrency Stats

Fetches the latest cryptocurrency data for a specific coin.

- **URL:** `/stats`
- **Method:** GET
- **Query Parameters:**
  - `coin` (required): The name of the cryptocurrency (e.g., bitcoin, ethereum, matic-network)

#### Sample Request

```
GET /stats?coin=bitcoin
```

#### Sample Response

```json
{
  "price": 50000,
  "marketCap": 1000000000000,
  "24hChange": 2.5
}
```

### 2. Get Price Deviation

Calculates the standard deviation of the last 100 price records for a specific coin.

- **URL:** `/deviation`
- **Method:** GET
- **Query Parameters:**
  - `coin` (required): The name of the cryptocurrency (e.g., bitcoin, ethereum, matic-network)

#### Sample Request

```
GET /deviation?coin=ethereum
```

#### Sample Response

```json
{
  "deviation": 150.25
}
```

## Error Handling

The API returns appropriate HTTP status codes and error messages in case of failures.

- 404: Data not found for the specified coin
- 500: Internal server error

## Data Update

Cryptocurrency data is fetched and stored every 2 hours using a cron job.

## Environment Variables

The following environment variables need to be set:

- `PORT`: The port on which the server will run (default: 7000)
- `MONGODB_URL`: MongoDB connection string
- `COINGECKO_API_KEY`: API key for CoinGecko

## Running the Server

1. Install dependencies:
   ```
   npm install
   ```

2. Set up environment variables in a `.env` file

3. Start the server:
   ```
   npm start
   ```

The server will start running on the specified port (default: 7000).
