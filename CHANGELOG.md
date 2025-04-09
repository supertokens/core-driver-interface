# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)


## [unreleased]

## [5.3.0]

- Adds APIs to bulk import users
  - GET `/bulk-import/users`
  - POST `/bulk-import/users`
  - GET `/bulk-import/users/count`
  - POST `/bulk-import/users/remove`
  - POST `/bulk-import/users/import`

## [5.2.0]

- Adds APIs related to OAuth2 Provider

## [5.1.1]

- Fixes response schema of thirdparty signInUp POST

## [5.1.0]

- Adds `/appid-<appid>/<tenantid>/recipe/dashboard/tenant/core-config` GET API.
- Adds optional `websiteDomain` and `apiDomain` query param to GET `/appid-<appId>/apiversion` API.
- Deprecates the recipe enabled booleans for ConnectionURIDomains, Apps and Tenants and now the `firstFactors` and `requiredSecondaryFactors` are used to control the login methods.
  - Deprecated APIs:
    - PUT `/recipe/multitenancy/connectionuridomain`
    - GET `/recipe/multitenancy/connectionuridomain/list`
    - PUT `/recipe/multitenancy/app`
    - GET `/recipe/multitenancy/app/list`
    - PUT `/appid-<appid>/recipe/multitenancy/tenant`
    - GET `/appid-<appid>/<tenantid>/recipe/multitenancy/tenant`
    - GET `/appid-<appid>/<tenantid>/recipe/multitenancy/tenant/list`
  - New v2 APIs replacing the deprecated APIs:
    - PUT `/recipe/multitenancy/connectionuridomain/v2`
    - GET `/recipe/multitenancy/connectionuridomain/list/v2`
    - PUT `/recipe/multitenancy/app/v2`
    - GET `/recipe/multitenancy/app/list/v2`
    - PUT `/appid-<appid>/recipe/multitenancy/tenant/v2`
    - GET `/appid-<appid>/<tenantid>/recipe/multitenancy/tenant/v2`
    - GET `/appid-<appid>/<tenantid>/recipe/multitenancy/tenant/list/v2`

## [5.0.0] - 2024-03-19

- `TOTP_NOT_ENABLED_ERROR` status is removed from the totp related APIs.
- In `/appid-<appId>/recipe/totp/device` POST, `deviceName` input is now optional. The response also includes `deviceName`.
- Adds `/recipe/totp/device/import` POST API.
- `INVALID_TOTP_ERROR`, `LIMIT_REACHED_ERROR` responses now include `currentNumberOfFailedAttempts` and `maxNumberOfFailedAttempts` in the response.
- Adds `/appid-<appId>/<tenantId>/recipe/signinup/code/check` POST API.
- Adds `consumedDevice` in the success response for `/appid-<appId>/<tenantId>/recipe/signinup/code/consume` POST API.
- `/appid-<appId>/<tenantId>/recipe/signinup/code/remove` POST API now accepts `preAuthSessionId` as input which can be used to remove code for a device.
- `/appid-<appId>/<tenantId>/recipe/session/remove` POST API can now only be called using public tenant if `revokeAcrossAllTenants` is set to true.
- `/appid-<appId>/<tenantId>/recipe/session/user` GET API can now only be called using public tenant if `fetchAcrossAllTenants` is set to true.
- Makes `useDynamicSigningKey` input mandatory in `/appid-<appId>/recipe/session/refresh` POST API.
- Adds `firstFactors` and `requiredSecondaryFactors` to the input of `/recipe/multitenancy/connectionuridomain` PUT, `/recipe/multitenancy/app` PUT and `/appid-<appId>/recipe/multitenancy/tenant` PUT APIs.
- Adds `firstFactors` and `requiredSecondaryFacrors` to the response of `/appid-<appId>/<tenantId>/recipe/multitenancy/tenant` GET API.

## [4.0.3]

- Adds an optional `useDynamicSigningKey` to the session refresh (`POST` `/appid-<appId>/recipe/session/refresh`) request body

## [4.0.2]

- Adds GET `/appid-<appId>/requests/stats` API

## [4.0.1]

- Fixes location of `isVerified` boolean in the third party signinup API request body.

## [4.0.0]

- Adds new APIs for account linking
  - GET `/appid-<appId>/recipe/accountlinking/user/primary/check`
  - GET `/appid-<appId>/recipe/accountlinking/user/link/check`
  - POST `/appid-<appId>/recipe/accountlinking/user/primary`
  - POST `/appid-<appId>/recipe/accountlinking/user/link`
  - POST `/appid-<appId>/recipe/accountlinking/user/unlink`

- Adds new APIs for query user
  - GET `/appid-<appId>/user/id`
  - GET `/appid-<appId>/<tenantId>/users/by-accountinfo`

- Deprecates following APIs
  - GET `/appid-<appId>/<tenantId>/recipe/user` (for all recipes)
  - GET `/appid-<appId>/<tenantId>/recipe/users/by-email`

- Updates to POST `/appid-<appId>/<tenantId>/recipe/signinup/code/consume`
  - Response `user` object is updated
  - Adds `recipeUserId` to the response

- Updates GET `/appid-<appId>/<tenantId>/recipe/user` (for all recipes)
  - Response `user` object is updated

- Updates PUT `/appid-<appId>/<tenantId>/recipe/user` (emailpassword and passwordless)
  - Renames input field `userId` to `recipeUserId`

- Updates PUT `/appid-<appId>/<tenantId>/recipe/user` (passwordless)
  - Returns new statuses `EMAIL_CHANGE_NOT_ALLOWED_ERROR` and `PHONE_NUMBER_CHANGE_NOT_ALLOWED_ERROR` along with `reason`

- Updates POST `/appid-<appId>/<tenantId>/recipe/signin`
  - Response `user` object is updated
  - Adds `recipeUserId` to the response

- Updates POST `/appid-<appId>/<tenantId>/recipe/signup`
  - Response `user` object is updated
  - Adds `recipeUserId` to the response

- Updates PUT `/appid-<appId>/<tenantId>/recipe/user` (emailpassword)
  - returns new status `EMAIL_CHANGE_NOT_ALLOWED_ERROR` along with `reason`

- Updates POST `/appid-<appId>/<tenantId>/recipe/user/password/reset/token`
  - Adds mandatory field `email` to the request body

- Updates POST `/appid-<appId>/<tenantId>/recipe/user/passwordhash/import`
  - Response `user` object is updated

- Adds POST `/appid-<appId>/<tenantId>/recipe/user/password/reset/token/consume` API

- Updates POST `/appid-<appId>/<tenantId>/recipe/signinup`
  - Adds mandatory `isVerified` field to the request body
  - Response `user` object is updated
  - Adds `recipeUserId` to the response
  - Returns new status `EMAIL_CHANGE_NOT_ALLOWED_ERROR` along with `reason`

- Updates GET `/appid-<appId>/<tenantId>/recipe/users/by-email`
  - Response `users` object is updated

- Updates GET `/appid-<appId>/<tenantId>/users`
  - Response `users` object is updated
  - Removes `recipeId` from the response

- Updates POST `/appid-<appId>/user/remove`
  - Adds optional parameter `removeAllLinkedAccounts` to the request body

- Updates POST `/appid-<appId>/<tenantId>/recipe/multitenancy/tenant/user`
  - Renames `userId` to `recipeUserId` in the request body

- Updates POST `/appid-<appId>/<tenantId>/recipe/multitenancy/tenant/user/remove`
  - Renames `userId` to `recipeUserId` in the request body

## [3.0.4]
- Updates `/appid-<appId>/<tenantId>/recipe/multitenancy/tenant` to also return `TENANT_NOT_FOUND_ERROR`

## [3.0.3]
- Updates following session APIs to include tenantId in response:
  - POST `/appid-<appId>/<tenantId>/recipe/session`
  - GET `/appid-<appId>/recipe/session`
  - POST `/appid-<appId>/recipe/session/verify`
  - POST `/appid-<appId>/recipe/session/refresh`
  - POST `/appid-<appId>/recipe/session/regenerate`
- Fixes GET `/appid-<appId>/<tenantId>/recipe/multitenancy/tenant` to include `coreConfig` and `tenantId`
- Fixes GET `/appid-<appId>/recipe/user/email/verify` to be app specific

## [3.0.2]
- Updates POST `/appid-<appId>/<tenantId>/recipe/session/remove` to include `revokeAcrossAllTenants` in the request
- Updates GET `/appid-<appId>/<tenantId>/recipe/session/user` to include `fetchAcrossAllTenants` in the query params
- Updates following APIs to be app specific:
  - GET and PUT `/appid-<appId>/recipe/session/data`
  - GET `/appid-<appId>/recipe/session`

## [3.0.1] - 2023-06-20

- Fixed `/recipe/multitenancy/tenant` GET

## [3.0.0] - 2023-06-02

- Adds `/appid-<appId>` or `/appid-<appId>/<tenantId>` prefix to some of the APIs as applicable. 
`appid-{appId}` and `{tenantId}` in all the APIs (wherever they are present) are optional. Their default values are `appid-public` and `public` respectively.
- Adds APIs for multitenancy recipe
  - adds `/recipe/multitenancy/connectionuridomain` PUT
  - adds `/recipe/multitenancy/connectionuridomain/remove` POST
  - adds `/recipe/multitenancy/connectionuridomain/list` GET
  - adds `/recipe/multitenancy/app` PUT
  - adds `/recipe/multitenancy/app/remove` POST
  - adds `/recipe/multitenancy/app/list` GET
  - adds `/recipe/multitenancy/tenant` PUT
  - adds `/recipe/multitenancy/tenant/remove` POST
  - adds `/recipe/multitenancy/tenant/list` GET
  - adds `/recipe/multitenancy/tenant/user` POST
  - adds `/recipe/multitenancy/tenant/user/remove` POST

- Adds APIs for creating and managing Thirdparty provider config for tenants
  - adds `/recipe/multitenancy/config/thirdparty` PUT
  - adds `/recipe/multitenancy/config/thirdparty/remove` POST

- Adds `tenantIds` in response of `/recipe/user` GET in emailpassword, passwordless and thirdparty recipes.
- Adds optional query param `includeAllTenants` to the `/users/count` GET API

- Removed deprecated APIs `/recipe/user` and `/recipe/users/count`

## [2.21.0] - 2023-05-12

### Fixed 
- Fixes `thirdParty` property in `thirdPartyUser` object

## [2.21.0] - 2023-04-05

- deprecate jwks endpoint in the jwt recipe (GET `/recipe/jwt/jwks`)
- add standard jwks endpoint (GET `/.well-known/jwks.json`)
- add `useDynamicSigningKey` into `createNewSession` (POST `/recipe/session`). This will be used instead of `access_token_signing_key_dynamic`
- add `useStaticSigningKey` into `createSignedJWT` (POST `/recipe/jwt`).
- removed handshake endpoint (POST `/recipe/handshake`)
- add checkDatabase into `verifySession` (POST `/recipe/session/verify`)
- removed old/unused props from responses related to signing keys & `id-refresh-token`

## [2.20.0] - 2023-03-30

### Added
- Core APIs:
  - `/user/search/tags` GET

### Updated
- Core APIs:
  - `/users` GET with the following query params:
    - `email` string
    - `phone` string
    - `provider` string
 

## [2.19.0] - 2023-03-24

- Core APIs:
  - `/users/count/active` GET
  - `/recipe/totp/device` POST
  - `/recipe/totp/device` PUT
  - `/recipe/totp/device/list` GET
  - `/recipe/totp/device/remove` POST
  - `/recipe/totp/verify` POST
  - `/recipe/totp/device/verify` POST

## [2.18.1] - 2023-03-1

### Fixed 

- Marks the `cdi-version` header param as optional

## [2.18.0] - 2023-02-21

- Core APIs:
  - `/recipe/dashboard/user` POST
  - `/recipe/dashboard/user` PUT
  - `/recipe/dashboard/user` DELETE
  - `/recipe/dashboard/users` GET
  - `/recipe/dashboard/session/verify` POST
  - `/recipe/dashboard/session` DELETE
  - `/recipe/dashboard/signin` POST
  - `/recipe/dashboard/user/sessions` GET
  
## [2.17.0] - 2023-01-04

### Added

- Core APIs:
  - `/ee/featureflag` GET
  - `/ee/license` PUT
  - `/ee/license` DELETE
  - `/ee/license` GET

## [2.16.2]

### Fixed
- In `/recipe/session/refresh` POST
  - `enableAntiCsrf` is now boolean
  - Marks `refreshToken` and `enableAntiCsrf` as required 

## [2.16.1]

### Fixed
- Marks `preAuthSessionId` as required in `/recipe/signinup/code/consume` POST

## [2.16.0]

### Added
- `/` GET

- EmailPassword APIs
  - adds `/recipe/user/passwordhash/import` POST

## [2.15.1]

### Updated
- UserIdMapping APIs
  - updates `/recipe/userid/map` POST with `force` boolean
  - updates `/recipe/userid/map/remove` POST with `force` boolean

## [2.15.0]

### Added

- UserId Mapping recipe:
- adds `/recipe/userid/map` POST
- adds `/recipe/userid/map/remove` POST
- adds `/recipe/userid/map` GET
- adds `/recipe/userid/external-user-id-info` PUT

## [2.14.0]

### Added

- User Roles recipe:
- adds `/recipe/user/role` PUT
- adds `/recipe/user/role/remove` POST 
- adds `/recipe/user/roles` GET 
- adds `/recipe/role/users` GET
- adds `/recipe/role ` PUT 
- adds `/recipe/role/permissions`GET 
- adds `/recipe/role/permissions/remove` POST 
- adds `/recipe/permission/roles` GET 
- adds `/recipe/role/remove` POST 
- adds `/recipe/roles` GET 

## [2.13.1]
### Fixed
- Marks `rid` optional in core APIs
- Marks `userId` in user metadata API as required.

## [2.13.0]

### Added

- User Metadata recipe
  - adds `/recipe/user/metadata` GET
  - adds `/recipe/user/metadata` PUT
  - adds `/recipe/user/metadata/remove` POST

## [2.12.0]

### Added 
- Adds `userId` in response of `/recipe/user/password/reset API`

## [2.11.0]

### Added 

- Passwordless recipe
  - adds `/signinup/code/consume` POST
  - adds `/signinup/code/remove`  POST
  - adds `/signinup/code`         POST
  - adds `/signinup/codes`        GET
  - adds `/signinup/codes/remove` POST

### Updated
- Core APIs
  - updates `/user`  GET with `passwordless` rid
  - updates `/users` GET with `rid` and new `user` type

## [2.10.0]

### Added 
- adds /user/remove POST

## [2.9.0]

### Added
- JWT recipe
  - adds JWT validity to `/recipe/jwt` POST
  - adds a new property `jwtSigningPublicKeyList` which lists valid JWT signing keys to the following API responses:
    - `/recipe/handshake`      POST
    - `/recipe/session`        POST
    - `/recipe/session/verify` POST 

### Updates
- Fixs response for `/users` GET

### Removed
- JWT recipe
  - removes `JWT_CREATION_ERROR` from `/recipe/jwt` POST response

## [2.8.0]

### Deprecated
- Emailpassword recipe
  - `/recipe/users/count` GET
  - `/recipe/users`       GET

- Thirdparty recipe
  - `/recipe/users/count` GET
  - `/recipe/users`       GET

- Session Recipe
- `/recipe/session/data`  GET
- `/recipe/jwt/data`      GET

### Removed 
- removes `isVerified` `boolean` from `/recipe/signinup` POST

### Added
- Core APIs
  - adds `/users/count` GET
  - adds `/users`       GET
  
- Session Recipe
  - adds `/recipe/session` GET

## [2.7.0]

### Added
- Third party recipe
  - adds `/recipe/signinup`    POST
  - adds `/recipe/user`        GET
  - adds `/recipe/users`       GET
  - adds`/recipe/users/count` GET

### Changed
- Email verification
  - Changed output of `/recipe/user/email/verify` to give `userId` instead of `user` object
  - Email verification APIs no longer return `UNKNOWN_USER_ID_ERROR`
  - Moved `/recipe/user/email/verify/token` to its own recipe
  - Moved `/recipe/user/email/verify` to its own recipe
  - Moved `/recipe/user/email/verify` to its own recipe

## [2.6.0]

### Updated
- `/recipe/handshake`       GET
- `/recipe/session`         POST
- `/recipe/session/verify`  POST
- `/recipe/session/refresh` POST

 [2.5.0]

### Added
- `/recipe/user/email/verify/token` POST
- `/recipe/user/email/verify`       POST
- `/recipe/user/email/verify`       GET
- `/recipe/users`                   GET
- `/recipe/count`                   GET

 [2.4.0]

### Removed

- `accessTokenPath`, `refreshTokenPath`, `cookieSecure`, `cookieSameSite`, `idRefreshTokenPath`, `cookieDomain`, `sessionExpiredStatusCode` from `handshakeInfo`

### Updated
- In `/config`, `NOT ALLOWED` => `NOT_ALLOWED`
- `/hello` API no longer requires `CDI` version
- `/handshake` => `/recipe/handshake`
- No longer require `deviceDriverInfo`
- Added `accessTokenValidity` and `refreshTokenValidity` to Handshake API
- `/session` => `/recipe/session`
- `/session/remove` => `/recipe/session/remove`
- `/session/verify` => `/recipe/session/verify`
- `/session/refresh` => `/recipe/session/refresh`
- `/session/user` => `/recipe/session/user`
- `/session/regenerate` => `/recipe/session/regenerate`
- /session/data => /recipe/session/data
- `/jwt/data` => `/recipe/jwt/data`

### Added 
- adds `/recipe/signin`
- adds `/recipe/signup`
- adds `/recipe/user`
- adds `/recipe/user/password/reset/token`
- adds `/recipe/user/password/reset`

### Removed
- Remove support code for older CDI versions:

