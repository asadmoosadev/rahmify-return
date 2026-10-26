# Rahmify return page

A one-page website that hands you back to the Rahmify app after you connect a
bank. TrueLayer only sends you back to `https://` web addresses, so it can't
open the app directly; on iPhone, that meant copying a link out of Safari.
This page forwards the result to `rahmify://callback`, so Safari just asks to
open Rahmify.

- It's static: no server code, no data, no cookies, no analytics, and nothing
  loaded from anywhere else (its content security policy blocks everything
  except its own few lines of script).
- The bank's one-time code passes through the page's address. That's safe:
  the code only works together with a secret key that never leaves the phone
  that started the sign-in (PKCE) and your TrueLayer client secret, and it can
  only be used once.

To use it, add `https://asadmoosadev.github.io/rahmify-return/` to your
TrueLayer app's Allowed redirect URIs, then in Rahmify go to Settings →
TrueLayer → Come straight back after bank sign-in.
