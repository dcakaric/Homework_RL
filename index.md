---
sidebar_position: 1
slug: /
---

# API Documentation

## List Available Analyzed Files

### Endpoint
```
GET /api/v1/download_samples/
```
This endpoind allows users to return a list of all files available for download as a JSON response.

### Request Format

#### Query Parameters

| Parameter | Required | Description | Type |
|-----------|----------|-------------|------|
| `date`    | Optional | Filters results to files analyzed on a specific date (`YYYY-MM-DD`). | string  |
| `user_id` | Optional | Filters results to files uploaded by a specific user. | string  |



#### Request Examples

##### cURL
```sh
curl -u z1000_user:z1000_password_example_123 -X GET "https://api.example.com/api/v1/download_samples/?date=2025-03-30&user_id=12345"
```
##### Python
```python
import requests

url = "https://api.example.com/api/v1/download_samples/"
params = {"date": "2025-03-30", "user_id": "12345"}
response = requests.get(url, auth=("z1000_user", "z1000_password_example_123"))
print(response.json())
```

### Response Format 

#### Response Examples

```json
{
  "files": [
    {
    "user_id": "12345", 
    "analyzed_date": "2025-03-30",
    "name": "malware.exe",
    "sample_id": "file123", 
    }, 
    {
    "user_id": "12345", 
    "analyzed_date": "2025-03-30",
    "name": "benign.pdf", 
    "sample_id": "file456",  }
  ]
}
```

## Access Analyzed Files for Download

This endpoint processes a JSON request containing file IDs and returns a JSON response with corresponding download links for each file

### Endpoint
```
POST /api/v1/download_samples/
```

### Request Format

#### Request body
```json
{
  "file_ids": ["file123", "file456"]
}
```

#### cURL
```sh
curl -u z1000_user:z1000_password_example_123 -X POST "https://api.example.com/api/v1/download_samples/" \
     -H "Content-Type: application/json" \
     -d '{"file_ids": ["file123", "file456"]}'
```

#### Python
```python
import requests

url = "https://api.example.com/api/v1/download_samples/"
data = {"file_ids": ["file123", "file456"]}
response = requests.post(url, json=data, auth=("z1000_user", "z1000_password_example_123"))
print(response.json())
```
### Response Format 

#### Response Examples
```json
{
  "downloads": [
    {"file_id": "file123", "download_url": "https://api.example.com/files/file123"},
    {"file_id": "file456", "download_url": "https://api.example.com/files/file456"}
  ]
}
```

## Error Responses
| Status Code | Message | Description |
|------------|---------|-------------|
| 400        | Bad Request | Invalid parameters in request. |
| 401        | Unauthorized | Authentication failed. |
| 403        | Forbidden | Access denied. |
| 404        | Not Found | File ID does not exist. |
| 500        | Server Error | An error occurred on the server. |






