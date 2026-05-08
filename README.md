# Event CRUD API

This project is a Flask REST API for a simple event management system. It uses an in-memory list of `Event` objects to simulate database behavior and supports creating, updating, and deleting events with JSON requests.

## Setup

```bash
python3 --version
pipenv install
pipenv shell
```

If you are not using pipenv, install Flask and pytest directly:

```bash
python3 -m pip install flask pytest
```

## Run the API

```bash
python3 app.py
```

The Flask server starts at `http://localhost:5000`.

## Routes

### Create an Event

`POST /events`

```bash
curl -X POST http://localhost:5000/events \
  -H "Content-Type: application/json" \
  -d '{"title": "Hackathon"}'
```

Successful response:

```json
{
  "id": 3,
  "title": "Hackathon"
}
```

Status code: `201 Created`

### Update an Event Title

`PATCH /events/<id>`

```bash
curl -X PATCH http://localhost:5000/events/1 \
  -H "Content-Type: application/json" \
  -d '{"title": "Hackathon 2025"}'
```

Successful response:

```json
{
  "id": 1,
  "title": "Hackathon 2025"
}
```

Status code: `200 OK`

### Delete an Event

`DELETE /events/<id>`

```bash
curl -X DELETE http://localhost:5000/events/2
```

Successful response: empty response body

Status code: `204 No Content`

## Error Responses

Missing JSON or missing `title`:

```json
{
  "error": "Event title is required"
}
```

Status code: `400 Bad Request`

Unknown event ID:

```json
{
  "error": "Event not found"
}
```

Status code: `404 Not Found`

## Test

Run the automated tests:

```bash
python3 -m pytest
```
