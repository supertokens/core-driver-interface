# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)

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

