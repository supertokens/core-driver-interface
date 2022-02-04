# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)

## [2.12.0]
- Adds `userId` in response of `/recipe/user/password/reset API`

## [2.11.0]

### Added 

- Passwordless recipe
  - `/signinup/code/consume` POST
  - `/signinup/code/remove`  POST
  - `/signinup/code`         POST
  - `/signinup/codes`        GET
  - `/signinup/codes/remove` POST

### Updated
- Core APIs
  - `/user`  GET with `passwordless` rid
  - `/users` GET with `rid` and new `user` type

## [2.10.0]

### Added 
- /user/remove POST

## [2.9.0]

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
- `isVerified` `boolean` from `/recipe/signinup` POST

### Added
- Core APIs
  - `/users/count` GET
  - `/users`       GET
  
- Session Recipe
  - `/recipe/session` GET

## [2.7.0]

### Added
- Third party recipe
  - `/recipe/signinup`    POST
  - `/recipe/user`        GET
  - `/recipe/users`       GET
  - `/recipe/users/count` GET

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
- New API: /recipe/signin
- New API: /recipe/signup
- New API: /recipe/user
- New API: /recipe/user/password/reset/token
- New API: /recipe/user/password/reset

### Removed
- Remove support code for older CDI versions:

