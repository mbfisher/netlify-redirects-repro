This is a repro of https://github.com/netlify/cli/issues/621

## Setup

1. `npm install`
2. `netlify dev`

## Repro

1. `curl -v localhost:8888/login` -> 200 OK ✅
2. `curl -v localhost:8888/` -> 302 /login ✅
3. `curl -v --cookie "nf_jwt=eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX21ldGFkYXRhIjp7Im5hbWUiOiJNaWtlIEZpc2hlciIsImVtYWlsIjpudWxsfSwiYXBwX21ldGFkYXRhIjp7ImF1dGhvcml6YXRpb24iOnsicm9sZXMiOlsiYXV0aG9yaXplZCJdfX0sImlhdCI6MTU3NDc1ODY0MSwiZXhwIjoxNTg0ODQ1MDQxfQ.w9yX-HgIhCELrpZsUN6lLO7A1tAf6cbCZwFJPMsTdQ0" localhost:8888/` -> 302 /login ❌

The token in the final requests:

```json
{
  "user_metadata": {
    "name": "Mike Fisher",
    "email": null
  },
  "app_metadata": {
    "authorization": {
      "roles": [
        "authorized"
      ]
    }
  },
  "iat": 1574758641,
  "exp": 1584845041
}
```
