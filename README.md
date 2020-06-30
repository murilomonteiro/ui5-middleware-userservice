# ui5-middleware-userservice

UI5 Middleware MIMIC userServices using configuration defined in configurations parameter

Middleware for [ui5-server](https://github.com/SAP/ui5-server), enabling proxy support.

## Install

```bash
npm install ui5-middleware-userservice --save-dev
```

## Configuration options (in `$yourapp/ui5.yaml`)

- key: `string`
  values `string` of key return json object

## Usage

1. Define the dependency in `$yourapp/package.json`:

```json
"devDependencies": {
    "ui5-middleware-userservice": "*"
},
"ui5": {
  "dependencies": [
    "ui5-middleware-userservice"
  ]
}
```

> As the devDependencies are not recognized by the UI5 tooling, they need to be listed in the `ui5 > dependencies` array. In addition, once using the `ui5 > dependencies` array you need to list all UI5 tooling relevant dependencies.

2. configure it in `$yourapp/ui5.yaml`:

```yaml
server:
  customMiddleware:
  - name: ui5-middleware-userservice
    mountPath: /services/userapi
    afterMiddleware: ui5-middleware-simpleproxy
    configuration:
      userID: "userID"
      displayName: "userID"
```