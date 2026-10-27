# cragradar-frontend-service

Kubernetes manifests that deploy the CragRadar frontend. The frontend is served by an unprivileged
nginx container, on the same hostname as the API, so no CORS setup is needed.

## Planned layout

```
base/
  deployment.yaml
  service.yaml
  ingress.yaml
  config.json             runtime config (API URL, OIDC issuer, client id), mounted from a ConfigMap
overlays/
  local/                  k3d
  cloud/                  OCI k3s
```

Deploy with `kubectl apply -k overlays/<target>`. Requires the platform from
`cragradar-backend-service` (Keycloak) to be installed.
