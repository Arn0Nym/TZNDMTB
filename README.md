# YourTube for TizenBrew

A small TizenBrew application module that opens the YourTube library as a top-level page in the TV web view. It does not use an iframe because the YourTube server currently sends `X-Frame-Options: DENY` and `frame-ancestors 'none'`.

## Add it to TizenBrew

1. Put this directory in a GitHub repository that the TV can access.
2. In TizenBrew on the TV, open **Module Manager** and add the GitHub module using `owner/repository@version`.
3. Restart TizenBrew and launch **YourTube**.

The app module is served by TizenBrew; it is not a separately installed `.wgt` tile in Samsung's Apps menu.

## HTTPS certificate requirement

The configured address is `https://192.168.1.43:8766/library`. During testing, Avast Web/Mail Shield intercepted the PC's HTTPS connection and presented a locally generated certificate issued by `Avast Web/Mail Shield Untrusted Root`. That does not identify the certificate the TV receives from the YourTube server, so it does not establish whether the TV trusts the server certificate. The plain HTTP URL returns 400. Check the HTTPS URL in the TV's browser if the module stalls; this module intentionally does not disable TLS verification.
