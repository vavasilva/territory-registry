# Territory Registry Service

## Usage

All responses will have the form

```json
{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happened"
}
```

Subsequent response definitions will only detail the expected value of the `data field`

### List all territories

**Definition**

`GET /territories`

**Response**

- `200 OK` on success

```json
[
    {
        "identifier": "1",
        "name": "Peter Parker",
        "dt_initial": "01/01/2019",
        "dt_final": "02/01/2019"
    },
    {
        "identifier": "2",
        "name": "Peter Parker",
        "dt_initial": "01/01/2019",
        "dt_final": "02/01/2019"
    }
]
```

### Registering a new territory

**Definition**

`POST /territories`

**Arguments**

- `"identifier":string` a globally unique identifier for this territory
- `"name":string` Name that stayed with a territory
- `"dt_inicial":string` date initial
- `"dt_final":string` date final

If a territory with the given identifier already exists, the existing territory will be overwritten.

**Response**

- `201 Created` on success

```json
{
    "identifier": "1",
    "name": "Peter Parker",
    "dt_initial": "01/01/2019",
    "dt_final": "02/01/2019"
}
```

## Lookup territory details

`GET /territories/<identifier>`

**Response**

- `404 Not Found` if the territory does not exist
- `200 OK` on success

```json
{
    "identifier": "1",
    "name": "Peter Parker",
    "dt_initial": "01/01/2019",
    "dt_final": "02/01/2019"
}
```

## Delete a territory

**Definition**

`DELETE /territories/<identifier>`

**Response**

- `404 Not Found` if the territory does not exist
- `204 No Content` on success
