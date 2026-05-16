# Company Formation Server

This server accepts company formation data and generates Articles of Incorporation for Delaware corporations.

## Setup

1. Install the required dependencies:
```bash
pip install -r requirements.txt
```

2. Run the server:
```bash
python app.py
```

## API Usage

Send a POST request to `/form-company` with a JSON payload in the following format:

```json
{
    "company_name": "Acme Corp, Inc.",
    "state_of_formation": "DE",
    "company_type": "corporation",
    "incorporator_name": "John Smith"
}
```
https://cs1060-hw6.vercel.app/


### Validation Rules:
- Company name: Can contain alphanumeric characters, spaces, commas, periods, apostrophes, and ampersands
- State of formation: Must be a valid US state or territory code
- Company type: Must be either "corporation" or "LLC"
- Incorporator name: Required field

### Supported Formations:
- Delaware corporations and LLCs
- California corporations and LLCs
- New York corporations and LLCs

### Response:
- Returns a PDF file containing the appropriate formation certificate for supported states
- Unsupported states or company types return a 400 error

## Example cURL Request:
```bash
curl -X POST http://localhost:5000/form-company \
  -H "Content-Type: application/json" \
  -d '{
    "company_name": "Acme Corp, Inc.",
    "state_of_formation": "DE",
    "company_type": "corporation",
    "incorporator_name": "John Smith"
  }'
```
