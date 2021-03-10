## Keycloak Setup

### Create and Configure Keycloak Realm

1. Log into admin portal at `https://<my-random-id.ngrok.io>/keycloak/auth`.
2. Create new realm by navigating to `Home --> Realm Drop Down (top left) --> Create New Realm`.
3. Enter Realm Name, such as `illumidesk`.
4. Click on `Configure` --> `Realm Settings`.
5. Ensure realm is toggled to `Enable`.
6. (Optional) Add `Display Name` and `HTML Display Name` values.
7. Click on `Login` tab.
8. Select the `none` setting for `Require SSL`.
9. Click on `Save`

### Create Keycloak Realm Client

1. Click on `Home` --> `Configure` --> `Clients` --> `Create`. The `Create` button is on the top right hand portion of the page.
2. Enter `Client ID`, such as `illumidesk-hub`
3. Ensure the `Enabled` option is toggled to `ON`.
4. (Optional) Add `Name` and `Description`.
5. Ensure the `Client Protocol` option is set to `openid-connect` (default).
6. Ensure the `Access Type` option is set to `credentials` (`public` is default).
7. Ensure `Standard Flow Enabled` is toggled to `ON`.
8. Ensure `Direct Access Grants Enabled` is toggled to `ON`.
9. (Optional) If testing with a public interface, update the `Root URL` setting with the external URL.
10. For `Base URL` enter `/`.
11. For `Web Origins` enter `*` (any origin).
