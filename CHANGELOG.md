# Release History

<!--
✨ Please add a bullet point describing your change.                                                             ✨
✨ You do not need to add a pull request reference or author information, this will be done automatically by CI. ✨
-->

## Unreleased: mitmproxy next

- fix: update log message with correct header name
  ([#7802](https://github.com/mitmproxy/mitmproxy/pull/7802), @kristof-mattei)
- Update deprecated `windows-2019` runner to `windows-2025`.
  ([#7801](https://github.com/mitmproxy/mitmproxy/pull/7801), @chedieck)
- Do not escape non-ascii characters in the JSON contentview.
  ([#7740](https://github.com/mitmproxy/mitmproxy/pull/7740), @mhils)
- Fix crash in mitmweb when no explicit Server-Connection is logged.
  ([#7734](https://github.com/mitmproxy/mitmproxy/pull/7734), @lups2000)
- Add syntax highlighting for CSS and JavaScript contentviews.
  ([#7749](https://github.com/mitmproxy/mitmproxy/pull/7749), @mhils)

## 25 May 2025: mitmproxy 12.1.1

- Fix a race condition when updating the flow list in mitmweb.
  ([#7729](https://github.com/mitmproxy/mitmproxy/pull/7729), @mhils)

## 24 May 2025: mitmproxy 12.1.0

- mitmweb now supports filtering by body contents (~b, ~bq, ~bs).
  ([#7704](https://github.com/mitmproxy/mitmproxy/pull/7704), @lups2000, @mhils)
- Fix raw response export incorrectly zeroing non-zero `Content-Length` header for HEAD requests.
  ([#7701](https://github.com/mitmproxy/mitmproxy/pull/7701), @sujaldev)
- Fix concurrent mitmweb instances overwrite each other's auth cookie.
  ([#7690](https://github.com/mitmproxy/mitmproxy/pull/7690), @turboOrange)

## 06 May 2025: mitmproxy 12.0.1

- Fix a crash when editing raw messages bodies in mitmproxy.
  ([#7697](https://github.com/mitmproxy/mitmproxy/pull/7697), @mhils)
- Added an option to pass the web token as `Authentication: Bearer ...` header
  ([#7681](https://github.com/mitmproxy/mitmproxy/pull/7681), @gschaer)
- In DNS proxy mode, user-provided addons now trigger before DNS resolution has taken place.
  ([#7685](https://github.com/mitmproxy/mitmproxy/pull/7685), @Florigolo)

## 29 April 2025: mitmproxy 12.0.0

### New Contentview System ([#7623](https://github.com/mitmproxy/mitmproxy/pull/7623), @mhils)

- Contentviews can now be interactive and re-encode prettified data.
  For example, the new Protobuf view pretty-prints to YAML, which the user
  can edit and then re-serialize into binary representation.
- Replace the existing gRPC and Protobuf contentviews with an interactive contentview that
  supports both existing proto definitions and completely unknown protos.
- The MsgPack contentview is now interactive, too.
- The contentview API has been drastically simplified.
  Contentviews now return a plain `str` with the prettified data.
  Syntax highlighting is now signaled off-band (and based on [tree-sitter]).
- Docs: Add new documentation page and API reference for contentviews.
- Contentviews can now be written in Rust for better performance and access to
  the crates ecosystem.

### Other Changes

- Add a new feature to store streamed bodies for requests and responses.
  ([#7637](https://github.com/mitmproxy/mitmproxy/pull/7637), @mkiami)
- Add support for TLS 1.3 Post Handshake Authentication.
  ([#7576](https://github.com/mitmproxy/mitmproxy/pull/7576), @mhils, @cataggar)
- Add search functionality to the documentation.
  ([#7603](https://github.com/mitmproxy/mitmproxy/pull/7603), @mhils)
- Introduce a new theme for docs.mitmproxy.org.
  ([#7593](https://github.com/mitmproxy/mitmproxy/pull/7593), @mhils)
- Add CRL entries to dummy cert when the upstream certificate has some.
  ([#7609](https://github.com/mitmproxy/mitmproxy/pull/7609), @Yepoleb, @JordanPlayz158)
- Fix a bug where mitmproxy would incorrectly send empty HTTP/2 data frames.
  ([#7574](https://github.com/mitmproxy/mitmproxy/pull/7574), @mhils, @Dieken)
- Enhance homebrew installation command for Brewfile users.
  ([#7566](https://github.com/mitmproxy/mitmproxy/pull/7566), @AntoineJT)
- Fix a bug where mitmdump would exit prematurely in server replay mode.
  ([#7571](https://github.com/mitmproxy/mitmproxy/pull/7571), @mhils)
- Fix a bug where WebSocket Messages view jumps to top when a message is received
  ([#7572](https://github.com/mitmproxy/mitmproxy/pull/7572), @DenizenB)
- Create content view for Socket.IO over WebSocket transport
  ([#7570](https://github.com/mitmproxy/mitmproxy/pull/7570), @DenizenB)
- Correctly forward HTTP_1_1_REQUIRED errors in HTTP/2 streams.
  ([#7575](https://github.com/mitmproxy/mitmproxy/pull/7575), @mhils)
- Fix a bug where HAR export would crash for malformed flows.
  ([#7666](https://github.com/mitmproxy/mitmproxy/pull/7666), @mhils)
- Fix a bug where mitmweb would crash when viewing flows with undefined headers.
  ([#7595](https://github.com/mitmproxy/mitmproxy/pull/7595), @emanuele-em)
- Fix a bug where mitmproxy does not listen on IPv4 and IPv6 by default in wireguard mode.
  ([#7589](https://github.com/mitmproxy/mitmproxy/pull/7589), @errorxyz)
- Adjust popover placement for browsers that support anchor positioning (Chrome, Edge)
  ([#7642](https://github.com/mitmproxy/mitmproxy/pull/7642), @lups2000)
- Fix mitmweb crash when searching or highlighting using ~h, ~hq, or ~hs.
  ([#7652](https://github.com/mitmproxy/mitmproxy/pull/7652), @lups2000)
- `mitmproxy.dns.Message` has been renamed to `mitmproxy.dns.DNSMessage`
  ([#7670](https://github.com/mitmproxy/mitmproxy/pull/7670), @mhils)
- Added support for selecting multiple flows in mitmweb using Ctrl+Click and Shift+Click. Multi-selection is now supported for deleting, duplicating, marking, reverting, replaying ,resuming, and aborting flows.
  ([#7319](https://github.com/mitmproxy/mitmproxy/pull/7319), @lups2000, @mhils)

[tree-sitter]: https://tree-sitter.github.io/tree-sitter/

## 17 February 2025: mitmproxy 11.1.3

- Update mitmproxy_rs dependency to fix several bugs in local capture mode.
  ([#7564](https://github.com/mitmproxy/mitmproxy/pull/7564), @mhils)
- Add documentation for local capture mode.
  ([#7540](https://github.com/mitmproxy/mitmproxy/pull/7540), @mhils)
- Revise documentation on proxy modes.
  ([#7545](https://github.com/mitmproxy/mitmproxy/pull/7545), @mhils)
- Add a log message to point Docker mitmweb users towards `web_password`.
  ([#7554](https://github.com/mitmproxy/mitmproxy/pull/7554), @mhils)
- Fix a bug where UTF-8 surrogates would crash the export addon.
  ([#7562](https://github.com/mitmproxy/mitmproxy/pull/7562), @mhils)
- Add help entries for all options in mitmweb that didn't have them.
  ([#7563](https://github.com/mitmproxy/mitmproxy/pull/7563), @mhils)

## 06 February 2025: mitmproxy 11.1.2

- [CVE-2025-23217](https://github.com/mitmproxy/mitmproxy/security/advisories/GHSA-wg33-5h85-7q5p):
  mitmweb's API now requires an authentication token by default.
  The mitmweb API is bound to localhost only, but @gronke found that an attacker can circumvent that restriction
  by tunneling requests through the proxy server itself in an [SSRF](https://en.wikipedia.org/wiki/Server-side_request_forgery)-style attack.
  ([fa89055](https://github.com/mitmproxy/mitmproxy/commit/fa89055e196d953f11fd241e36ee37858993486a), @mhils)
- Add (optional) password protection for mitmweb. The `web_password` option replaces the randomly-generated token
  authentication with a fixed secret that survives mitmproxy restarts.
  ([0bd573a](https://github.com/mitmproxy/mitmproxy/commit/0bd573a5995f61d82f5157e927b0eb93cdc4ebab), @mhils)
- mitmweb can now be hosted under arbitrary domains, the previously-used DNS rebind protection is not required anymore.
  ([62693af](https://github.com/mitmproxy/mitmproxy/commit/62693aff9a38ad0bb36716569fc627f26e489ccc), @mhils)
- Security Hardening: mitmweb's `xsrf_token` cookie is now `HttpOnly; SameSite=Strict`.
  ([#7491](https://github.com/mitmproxy/mitmproxy/pull/7491), @mhils)
- We now provide standalone binaries for Linux arm64.
  ([#7484](https://github.com/mitmproxy/mitmproxy/pull/7484), @mhils)
- Standalone binaries are now compiled with Python 3.13.
  ([#7485](https://github.com/mitmproxy/mitmproxy/pull/7485), @mhils)
- Fix console freezing due to DNS queries with an empty question section.
  ([#7497](https://github.com/mitmproxy/mitmproxy/pull/7497), @sujaldev)
- Add mitmweb tutorial to docs.
  ([#7509](https://github.com/mitmproxy/mitmproxy/pull/7509), @EstherRoeth)
- Fixed a bug that caused mitmproxy to crash when loading prior knowledge h2 flows.
  ([#7514](https://github.com/mitmproxy/mitmproxy/pull/7514), @sujaldev)
- Fix a bug where mitmproxy would get stuck in secure web proxy mode when using `ignore_hosts` or `allow_hosts`.
  ([#7519](https://github.com/mitmproxy/mitmproxy/pull/7519), @mhils)
- Copy request/response data to the clipboard in mitmweb
  ([#7352](https://github.com/mitmproxy/mitmproxy/pull/7352), @lups2000)
- Fix a bug where exporting a curl or httpie command with escaped characters would lead to different data being sent.
  ([#7520](https://github.com/mitmproxy/mitmproxy/pull/7520), @proteusvacuum)

## 05 February 2025: mitmproxy 11.1.1

- Yanked. Identical to 11.1.2, but failed to deploy in CI.

## 12 January 2025: mitmproxy 11.1.0

- **Local Capture Mode** is now available on Linux as well.
  ([#7440](https://github.com/mitmproxy/mitmproxy/pull/7440), @mhils)
- mitmproxy now requires Python 3.12 or above.
  ([#7440](https://github.com/mitmproxy/mitmproxy/pull/7440), @mhils)
- Add cache-busting for mitmweb's front end code.
  ([#7386](https://github.com/mitmproxy/mitmproxy/pull/7386), @mhils)
- Clicking the URL in mitmweb now places the cursor at the current position instead of selecting the entire URL.
  ([#7385](https://github.com/mitmproxy/mitmproxy/pull/7385), @lups2000)
- Add missing status codes
  ([#7455](https://github.com/mitmproxy/mitmproxy/pull/7455), @jwadolowski)
- All filter expressions are now case-insensitive by default.
  Users can opt into case-sensitive filters by setting MITMPROXY_CASE_SENSITIVE_FILTERS=1
  as an environment variable.
  ([#7458](https://github.com/mitmproxy/mitmproxy/pull/7458), @mhils, @AdityaPatadiya)
- Remove filter expression lowercasing in block_list addon
  ([#7456](https://github.com/mitmproxy/mitmproxy/pull/7456), @jwadolowski)
- Remove check for status codes in the blocklist add-on.
  ([#7453](https://github.com/mitmproxy/mitmproxy/pull/7453), @lups2000, @AdityaPatadiya)
- Prompt user before clearing screen
  ([#7445](https://github.com/mitmproxy/mitmproxy/pull/7445), @errorxyz)

## 05 December 2024: mitmproxy 11.0.2

- Stop sorting keys in JSON contentview
  ([#7346](https://github.com/mitmproxy/mitmproxy/pull/7346), @injust)
- Fix a bug where a custom CA would raise an error.
  ([#7355](https://github.com/mitmproxy/mitmproxy/pull/7355), @nneonneo)
- Fix a bug where the mitmproxy UI would crash on negative durations.
  ([#7358](https://github.com/mitmproxy/mitmproxy/pull/7358), @mhils)
- Allow technically invalid HTTP transfer encodings in requests if `validate_inbound_headers` is disabled.
  ([#7361](https://github.com/mitmproxy/mitmproxy/pull/7361), [#7373](https://github.com/mitmproxy/mitmproxy/pull/7373), @mhils)
- Fix a bug in windows management in mitmproxy TUI whereby the help window does not appear if "?" is pressed within the overlay
  ([#6500](https://github.com/mitmproxy/mitmproxy/pull/6500), @emanuele-em)

## 24 November 2024: mitmproxy 11.0.1

- Tighten HTTP detection heuristic to better support custom TCP-based protocols.
  ([#7228](https://github.com/mitmproxy/mitmproxy/pull/7228), @fatanugraha)
- Implement stricter validation of HTTP headers to harden against request smuggling attacks.
  ([#7345](https://github.com/mitmproxy/mitmproxy/issues/7345), @mhils)
- Increase HTTP/2 default flow control window size, fixing performance issues.
  ([#7317](https://github.com/mitmproxy/mitmproxy/pull/7317), @sujaldev)
- Fix a bug where mitmproxy would incorrectly report that TLS 1.0 and 1.1 are not supported
  with the current OpenSSL build.
  ([#7241](https://github.com/mitmproxy/mitmproxy/pull/7241), @mhils)
- Docker: Update image to Python 3.13 on Debian Bookworm.
  ([#7242](https://github.com/mitmproxy/mitmproxy/pull/7242), @mhils)
- Add a `tun` proxy mode that creates a virtual network device on Linux for transparent proxying.
  ([#7278](https://github.com/mitmproxy/mitmproxy/pull/7278), @mhils)
- `browser.start` command now supports Firefox.
  ([#7239](https://github.com/mitmproxy/mitmproxy/pull/7239), @sujaldev)
- Fix interaction of the `modify_headers` and `stream_large_bodies` options.
  This may break users of `modify_headers` that rely on filters referencing the message body.
  We expect this to be uncommon, but please make yourself heard if that's not the case.
  ([#7286](https://github.com/mitmproxy/mitmproxy/pull/7286), @lukant)
- Fix a crash when handling corrupted compressed body in savehar addon and its tests.
  ([#7320](https://github.com/mitmproxy/mitmproxy/pull/7320), @8192bytes)
- Remove dependency on `protobuf` library as it was no longer being used.
  ([#7327](https://github.com/mitmproxy/mitmproxy/pull/7327), @matthew16550)

## 02 October 2024: mitmproxy 11.0.0

- mitmproxy now supports transparent HTTP/3 proxying.
  ([#7202](https://github.com/mitmproxy/mitmproxy/pull/7202), @errorxyz, @meitinger, @mhils)
- Add HTTP3 support in HTTPS reverse-proxy mode.
  ([#7114](https://github.com/mitmproxy/mitmproxy/pull/7114), @errorxyz)
- mitmproxy now officially supports Python 3.13.
  ([#6934](https://github.com/mitmproxy/mitmproxy/pull/6934), @mhils)
- Tighten HTTP detection heuristic to better support custom TCP-based protocols.
  ([#7087](https://github.com/mitmproxy/mitmproxy/pull/7087))
- Add `show_ignored_hosts` option to display ignored flows in the UI.
  This option is implemented as a temporary workaround and will be removed in the future.
  ([#6720](https://github.com/mitmproxy/mitmproxy/pull/6720), @NicolaiSoeborg)
- Fix slow tnetstring parsing in case of very large tnetstring.
  ([#7121](https://github.com/mitmproxy/mitmproxy/pull/7121), @mik1904)
- Add `getaddrinfo`-based fallback for DNS resolution if we are unable to
  determine the operating system's name servers.
  ([#7122](https://github.com/mitmproxy/mitmproxy/pull/7122), @mhils)
- Improve the error message when users specify the `certs` option without a matching private key.
  ([#7073](https://github.com/mitmproxy/mitmproxy/pull/7073), @mhils)
- Fix a bug where intermediate certificates would not be transmitted when using QUIC.
  ([#7073](https://github.com/mitmproxy/mitmproxy/pull/7073), @mhils)
- Fix a bug where fragmented QUIC client hellos were not handled properly.
  ([#7067](https://github.com/mitmproxy/mitmproxy/pull/7067), @errorxyz)
- Emit a warning when users configure a TLS version that is not supported by the
  current OpenSSL build.
  ([#7139](https://github.com/mitmproxy/mitmproxy/pull/7139), @mhils)
- Fix a bug where mitmproxy would crash when receiving `STOP_SENDING` QUIC frames.
  ([#7119](https://github.com/mitmproxy/mitmproxy/pull/7119), @mhils)
- Fix error when unmarking all flows.
  ([#7192](https://github.com/mitmproxy/mitmproxy/pull/7192), @bburky)
- Add addon to update the alt-svc header in reverse mode.
  ([#7093](https://github.com/mitmproxy/mitmproxy/pull/7093), @errorxyz)
- Do not send unnecessary empty data frames when streaming HTTP/2.
  ([#7196](https://github.com/mitmproxy/mitmproxy/pull/7196), @rubu)
- Fix a bug where mitmproxy would ignore Ctrl+C/SIGTERM on OpenBSD.
  ([#7130](https://github.com/mitmproxy/mitmproxy/pull/7130), @catap)
- Fix of measurement unit in HAR import, duration is in milliseconds.
  ([#7179](https://github.com/mitmproxy/mitmproxy/pull/7179), @dstd)
- `Connection.tls_version` now is `QUICv1` instead of `QUIC` for QUIC.
  ([#7201](https://github.com/mitmproxy/mitmproxy/pull/7201), @mhils)
- Add support for full mTLS with client certs between client and mitmproxy.
  ([#7175](https://github.com/mitmproxy/mitmproxy/pull/7175), @Kriechi)
- Update documentation adding a list of all possibile web_columns.
  ([#7205](https://github.com/mitmproxy/mitmproxy/pull/7205), @lups2000, @Abhishek-Bohora)

## 02 August 2024: mitmproxy 10.4.2

- Fix a crash on startup when mitmproxy is unable to determine the OS' DNS servers
  ([#7066](https://github.com/mitmproxy/mitmproxy/pull/7066), @errorxyz)

## 29 July 2024: mitmproxy 10.4.1

- Fix a bug where macOS local mode would not start up on macOS.
  ([#7045](https://github.com/mitmproxy/mitmproxy/pull/7045), @mhils)
- Fix UDP error handling when we learn that the remote has disconnected.
  ([#7045](https://github.com/mitmproxy/mitmproxy/pull/7045), @mhils)
- Container images are now published to both Docker Hub and GitHub Container Registry.
  ([#7061](https://github.com/mitmproxy/mitmproxy/pull/7061), @mhils)

## 25 July 2024: mitmproxy 10.4.0

* Add support for DNS over TCP.
  ([#6935](https://github.com/mitmproxy/mitmproxy/pull/6935), @errorxyz)
* Add first MVP new Capture Tab in mitmweb
  ([#6999](https://github.com/mitmproxy/mitmproxy/pull/6999), @lups2000)
* Add `HttpConnectedHook` and `HttpConnectErrorHook`.
  ([#6930](https://github.com/mitmproxy/mitmproxy/pull/6930), @errorxyz)
* Fix non-linear growth in processing time for large HTTP bodies.
  ([#6952](https://github.com/mitmproxy/mitmproxy/pull/6952), @jackfromeast)
* Fix a bug where connections would be incorrectly ignored with `allow_hosts`.
  ([#7002](https://github.com/mitmproxy/mitmproxy/pull/7002), @JarLob, @mhils)
* Fix zstd decompression to read across frames.
  ([#6921](https://github.com/mitmproxy/mitmproxy/pull/6921), @zendai)
* Handle certificates we cannot parse more gracefully.
  ([#6994](https://github.com/mitmproxy/mitmproxy/pull/6994), @mhils)
* Parse compressed domain names in ResourceRecord data.
  ([#6954](https://github.com/mitmproxy/mitmproxy/pull/6954), @errorxyz)
* Fix a bug where mitmweb's flow list would not stay at the bottom.
  ([#7008](https://github.com/mitmproxy/mitmproxy/pull/7008), @mhils)
* Fix a bug where SSH connections would be incorrectly handled as HTTP.
  ([#7041](https://github.com/mitmproxy/mitmproxy/pull/7041), @mhils)
* Skip UTF-8 byte-order marks (BOM) when loading HAR files.
  ([#6897](https://github.com/mitmproxy/mitmproxy/pull/6897), @dstd)
* Allow `typing.Sequence[str]` to be an editable option.
  ([#7001](https://github.com/mitmproxy/mitmproxy/pull/7001), @errorxyz)
* Add Host header to CONNECT requests.
  ([#7021](https://github.com/mitmproxy/mitmproxy/pull/7021), @petsneakers)
* Support all query types in DNS mode.
  ([#6975](https://github.com/mitmproxy/mitmproxy/pull/6975), @errorxyz)
* Fix a bug where mitmproxy would crash for pipelined HTTP flows.
  ([#7031](https://github.com/mitmproxy/mitmproxy/pull/7031), @gdiepen, @mhils)
* Add an optional "index" column for mitmweb.
  ([#7039](https://github.com/mitmproxy/mitmproxy/pull/7039), @mhils)

## 12 June 2024: mitmproxy 10.3.1

* Release tags are now prefixed with `v` again.
  ([#6810](https://github.com/mitmproxy/mitmproxy/pull/6810), @mhils)
* Fix a bug where mitmproxy would not exit when `-n` is passed.
  ([#6819](https://github.com/mitmproxy/mitmproxy/pull/6819), @mhils)
* Set the `unbuffered` (stdout/stderr) flag for the `mitmdump` PyInstaller build.
  ([#6821](https://github.com/mitmproxy/mitmproxy/pull/6821), @Prinzhorn)
* Fix a bug where client replay would not work with proxyauth.
  ([#6866](https://github.com/mitmproxy/mitmproxy/pull/6866), @mhils)
* Fix slowdown when sending large amounts of data over HTTP/2.
  ([#6875](https://github.com/mitmproxy/mitmproxy/pull/6875), @aib)
* Add an option to strip HTTPS records from DNS responses to block encrypted ClientHellos.
  ([#6876](https://github.com/mitmproxy/mitmproxy/pull/6876), @errorxyz)
* Add an API to parse HTTPS records from DNS RDATA.
  ([#6884](https://github.com/mitmproxy/mitmproxy/pull/6884), @errorxyz)
* Fix flow export in mitmweb for Safari
  ([#6917](https://github.com/mitmproxy/mitmproxy/pull/6917), @mhils, @canyesilyurt)
* Releases now come with a Sigstore attestations file to demonstrate build provenance.
  ([f05c050](https://github.com/mitmproxy/mitmproxy/commit/f05c050f615b9ab9963707944c893bc94e738525), @mhils)

## 17 April 2024: mitmproxy 10.3.0

* Add support for editing non text files in a hex editor
  ([#6768](https://github.com/mitmproxy/mitmproxy/pull/6768), @wnyyyy)
* Add `server_connect_error` hook that is triggered when connection establishment fails.
  ([#6806](https://github.com/mitmproxy/mitmproxy/pull/6806), @haanhvu, @spacewasp, @mhils)
* Add section in mitmweb for rendering, adding and removing a comment
  ([#6709](https://github.com/mitmproxy/mitmproxy/pull/6709), @lups2000)
* Fix multipart form content view being unusable.
  ([#6653](https://github.com/mitmproxy/mitmproxy/pull/6653), @DaniElectra)
* Documentation Improvements on CA Certificate Generation
  ([#5370](https://github.com/mitmproxy/mitmproxy/pull/5370), @zioalex)
* Make it possible to read flows from stdin with mitmweb.
  ([#6732](https://github.com/mitmproxy/mitmproxy/pull/6732), @jaywor1)
* Update aioquic dependency to >= 1.0.0, < 2.0.0.
  ([#6747](https://github.com/mitmproxy/mitmproxy/pull/6747), @jlaine)
* Fix a bug where async `client_connected` handlers would crash mitmproxy.
  ([#6749](https://github.com/mitmproxy/mitmproxy/pull/6749), @mhils)
* Add button to close flow details panel
  ([#6734](https://github.com/mitmproxy/mitmproxy/pull/6734), @lups2000)
* Ignore SIGPIPE signals when there is lots of traffic.
  Socket errors are handled directly and do not require extra signals
  that generate noise.
  ([#6764](https://github.com/mitmproxy/mitmproxy/pull/6764), @changsin)
* Add primitive websocket interception and modification
  ([#6766](https://github.com/mitmproxy/mitmproxy/pull/6766), @errorxyz)
* Add support for exporting websocket messages when using "raw" export.
  ([#6767](https://github.com/mitmproxy/mitmproxy/pull/6767), @txrp0x9)
* The "save body" feature now also includes WebSocket messages.
  ([#6767](https://github.com/mitmproxy/mitmproxy/pull/6767), @txrp0x9)
* Fix compatibility with older cryptography versions and silence a DeprecationWarning on Python <3.11.
  ([#6790](https://github.com/mitmproxy/mitmproxy/pull/6790), @mhils)
* Fix a bug when proxying unicode domains.
  ([#6796](https://github.com/mitmproxy/mitmproxy/pull/6796), @mhils)


## 07 March 2024: mitmproxy 10.2.4

* Fix a bug where errors during startup would not be displayed when running mitmproxy.
  ([#6719](https://github.com/mitmproxy/mitmproxy/pull/6719), @mhils)
* Use newer cryptography APIs to avoid CryptographyDeprecationWarnings.
  This bumps the minimum required version to cryptography 42.0.
  ([#6718](https://github.com/mitmproxy/mitmproxy/pull/6718), @mhils)


## 06 March 2024: mitmproxy 10.2.3

* Fix a regression where `allow_hosts`/`ignore_hosts` would break with IPv6 connections.
  ([#6614](https://github.com/mitmproxy/mitmproxy/pull/6614), @dqxpb)
* Fix bug where failed CONNECT request URLs are saved to HAR files incorrectly.
  ([#6599](https://github.com/mitmproxy/mitmproxy/pull/6599), @basedBaba)
* Add an arm64 variant for the precompiled macOS app.
  ([#6633](https://github.com/mitmproxy/mitmproxy/pull/6633), @mhils)
* Fix duplicate answers being returned in DNS queries.
  ([#6648](https://github.com/mitmproxymitmproxy/pull/6648), @sujaldev)
* Fix bug where wireguard config is generated with incorrect endpoint when two or more NICs are active.
  ([#6659](https://github.com/mitmproxy/mitmproxy/pull/6659), @basedBaba)
* Fix a regression when leaf cert creation would fail with intermediate CAs in `ca_file`.
  ([#6666](https://github.com/mitmproxy/mitmproxy/pull/6666), @manselmi)
* Add `content_view_lines_cutoff` option to mitmdump
  ([#6692](https://github.com/mitmproxy/mitmproxy/pull/6692), @errorxyz)
* Allow runtime modifications of HTTP flow filters for server replays
  ([#6695](https://github.com/mitmproxy/mitmproxy/pull/6695), @errorxyz)
* Fix bug view options menu in case of overflow
  ([#6697](https://github.com/mitmproxy/mitmproxy/pull/6697), @lups2000)
* Allow --allow-hosts and --ignore-hosts to work together
  ([#6711](https://github.com/mitmproxy/mitmproxy/pull/6711), @dstd)


## 21 January 2024: mitmproxy 10.2.2

* Fix a regression where clientplayback would break due to eager task execution.
  ([#6605](https://github.com/mitmproxy/mitmproxy/pull/6605), @mhils)
* Fix a regression where WebSocket connections would break due to eager task execution.
  ([#6609](https://github.com/mitmproxy/mitmproxy/pull/6609), @mhils)
* Fix bug where insecure HTTP requests are saved incorrectly when exporting to HAR files.
  ([#6578](https://github.com/mitmproxy/mitmproxy/pull/6578), @DaniElectra)
* `allow_hosts`/`ignore_hosts` option now matches against the full `host:port` string.
  ([#6594](https://github.com/mitmproxy/mitmproxy/pull/6594), @LouisAsanaka)


## 06 January 2024: mitmproxy 10.2.1

* Fix a regression introduced in mitmproxy 10.2.0: WireGuard servers
  now bind to all interfaces again.
  ([#6587](https://github.com/mitmproxy/mitmproxy/pull/6587), @mhils)
* Remove stale reference to `ctx.log` in addon documentation.
  ([#6552](https://github.com/mitmproxy/mitmproxy/pull/6552), @brojonat)
* Fix a bug where a traceback is shown during shutdown.
  ([#6581](https://github.com/mitmproxy/mitmproxy/pull/6581), @mhils)


## 04 January 2024: mitmproxy 10.2.0

* *Local Redirect Mode* is now officially available on
  [macOS](https://mitmproxy.org/posts/local-redirect/macos/)
  and [Windows](https://mitmproxy.org/posts/local-redirect/windows/).
  See the linked blog posts for details. (@emanuele-em, @mhils)
* UDP streams are now backed by a new implementation in `mitmproxy_rs`.
  This represents a major API change as UDP traffic is now exposed as streams
  instead of a callback for each packet. (@mhils)
* Fix a regression from mitmproxy 10.1.6 where `ignore_hosts` would terminate requests
  instead of forwarding them.
  ([#6559](https://github.com/mitmproxy/mitmproxy/pull/6559), @mhils)
* `ignore_hosts` now waits for the entire HTTP headers if it suspects the connection to be HTTP.
  ([#6559](https://github.com/mitmproxy/mitmproxy/pull/6559), @mhils)


## 14 December 2023: mitmproxy 10.1.6

* Fix compatibility with Windows Schannel clients, which previously got
  confused by CA and leaf certificate sharing the same Subject Key Identifier.
  ([#6549](https://github.com/mitmproxy/mitmproxy/pull/6549), @driuba and @mhils)
* Change keybinding for exporting flow from "e" to "x" to avoid conflict with "edit" keybinding.
  ([#6225](https://github.com/mitmproxy/mitmproxy/issues/6225), @Llama1412)
* Fix bug where response flows from HAR files had incorrect `content-length` headers
  ([#6548](https://github.com/mitmproxy/mitmproxy/pull/6548), @zanieb)
* Improved handling for `allow_hosts`/`ignore_hosts` options in WireGuard mode (#5930).
  ([#6513](https://github.com/mitmproxy/mitmproxy/pull/6513), @dsphper)
* Fix a bug where TCP connections were not closed properly.
  ([#6543](https://github.com/mitmproxy/mitmproxy/pull/6543), @mhils)
* DNS resolution is now exempted from `ignore_hosts` in WireGuard Mode.
  ([#6513](https://github.com/mitmproxy/mitmproxy/pull/6513), @dsphper)
* Fix case sensitivity of URL added to blocklist
  ([#6493](https://github.com/mitmproxy/mitmproxy/pull/6493), @emanuele-em)
* Fix a bug where logging was stopped prematurely during shutdown.
  ([#6541](https://github.com/mitmproxy/mitmproxy/pull/6541), @mhils)
* For plaintext traffic, `ignore_hosts` now also takes HTTP/1 host headers into account.
  ([#6513](https://github.com/mitmproxy/mitmproxy/pull/6513), @dsphper)
* Fix empty cookie attributes being set to `Key=` instead of `Key`
  ([#5084](https://github.com/mitmproxy/mitmproxy/pull/5084), @Speedlulu)
* Scripts with relative paths are now loaded relative to the config file and not where the command is ran
  ([#4860](https://github.com/mitmproxy/mitmproxy/pull/4860), @Speedlulu)
* Fix `mitmweb` splitter becoming drag and drop.
  ([#6492](https://github.com/mitmproxy/mitmproxy/pull/6492), @xBZZZZ)
* Enhance documentation and add alert log messages when stream_large_bodies and modify_body are set
  ([#6514](https://github.com/mitmproxy/mitmproxy/pull/6514), @rosydawn6)

### Breaking Changes

* Subject Alternative Names are now represented as `cryptography.x509.GeneralNames` instead of `list[str]`
  across the codebase. This fixes a regression introduced in mitmproxy 10.1.1 related to punycode domain encoding.
  ([#6537](https://github.com/mitmproxy/mitmproxy/pull/6537), @mhils)


## 14 November 2023: mitmproxy 10.1.5

* Remove stray `replay-extra` from CLI status bar.
  ([37d62ce](https://github.com/mitmproxy/mitmproxy/commit/37d62ce73ebd57780cff5ecf8b2ee57ec7d8ab30), @mhils)


## 13 November 2023: mitmproxy 10.1.4

* Fix a hang/freeze in the macOS distributions when doing TLS negotiation.
  ([#6480](https://github.com/mitmproxy/mitmproxy/pull/6480), @mhils)
* Update savehar addon to fix creating corrupt har files caused by empty response content
  ([#6459](https://github.com/mitmproxy/mitmproxy/pull/6459), @lain3d)
* Update savehar addon to handle scenarios where "path" key in cookie
  attrs dict is missing.
  ([#6458](https://github.com/mitmproxy/mitmproxy/pull/6458), @pogzyb)
* Add `server_replay_extra` option to serverplayback to define behaviour
  when replayable response is missing.
  ([#6465](https://github.com/mitmproxy/mitmproxy/pull/6465), @dkarandikar)


## 04 November 2023: mitmproxy 10.1.3

* Fix a bug introduced in mitmproxy 10.1.2 where mitmweb would fail to establish
  a WebSocket connection. Affected users may need to clear their browser cache
  or hard-reload mitmweb (Ctrl+Shift+R).
  ([#6454](https://github.com/mitmproxy/mitmproxy/pull/6454), @mhils)


## 03 November 2023: mitmproxy 10.1.2

* Add a raw hex stream contentview.
  ([#6389](https://github.com/mitmproxy/mitmproxy/pull/6389), @mhils)
* Add a contentview for DNS-over-HTTPS.
  ([#6389](https://github.com/mitmproxy/mitmproxy/pull/6389), @mhils)
* Replaced standalone mitmproxy binaries on macOS with an app bundle
  that contains the mitmproxy/mitmweb/mitmdump CLI tools.
  This change was necessary to support macOS code signing requirements.
  Homebrew remains the recommended installation method.
  ([#6447](https://github.com/mitmproxy/mitmproxy/pull/6447), @mhils)
* Fix certificate generation to work with strict mode OpenSSL 3.x clients
  ([#6410](https://github.com/mitmproxy/mitmproxy/pull/6410), @mmaxim)
* Fix path() documentation that the return value might include the query string
  ([#6412](https://github.com/mitmproxy/mitmproxy/pull/6412), @tddschn)
* mitmproxy now officially supports Python 3.12.
  ([#6434](https://github.com/mitmproxy/mitmproxy/pull/6434), @mhils)
* Fix root-relative URLs so that mitmweb can run in subdirectories.
  ([#6411](https://github.com/mitmproxy/mitmproxy/pull/6411), @davet2001)
* Add an optional parameter(ldap search filter key) to ProxyAuth-LDAP.
  ([#6428](https://github.com/mitmproxy/mitmproxy/pull/6428), @outlaws-bai)
* Fix a regression when using the proxyauth addon with clients that (rightfully) reuse connections.
  ([#6432](https://github.com/mitmproxy/mitmproxy/pull/6432), @mhils)


## 27 September 2023: mitmproxy 10.1.1

* Fix certificate generation for punycode domains.
  ([#6382](https://github.com/mitmproxy/mitmproxy/pull/6382), @mhils)
* Fix a bug that would crash mitmweb when opening options.
  ([#6386](https://github.com/mitmproxy/mitmproxy/pull/6386), @mhils)


## 24 September 2023: mitmproxy 10.1.0

* Add support for reading HAR files using the existing flow loading APIs, e.g. `mitmproxy -r example.har`.
  ([#6335](https://github.com/mitmproxy/mitmproxy/pull/6335), @stanleygvi)
* Add support for writing HAR files using the `save.har` command and the `hardump` option for mitmdump.
  ([#6368](https://github.com/mitmproxy/mitmproxy/pull/6368), @stanleygvi)
* Packaging changes:
  - `mitmproxy-rs` does not depend on a protobuf compiler being available anymore,
    we're now also providing a working source distribution for all platforms.
  - On macOS, `mitmproxy-rs` now depends on `mitmproxy-macos`. We only provide binary wheels for this package because
    it contains a code-signed system extension. Building from source requires a valid Apple Developer Id, see CI for
    details.
  - On Windows, `mitmproxy-rs` now depends on `mitmproxy-windows`. We only provide binary wheels for this package to
    simplify our deployment process, see CI for how to build from source.

  ([#6303](https://github.com/mitmproxy/mitmproxy/issues/6303), @mhils)
* Increase maximum dump file size accepted by mitmweb
  ([#6373](https://github.com/mitmproxy/mitmproxy/pull/6373), @t-wy)


## 04 August 2023: mitmproxy 10.0.0

* Add experimental support for HTTP/3 and QUIC.
  ([#5435](https://github.com/mitmproxy/mitmproxy/issues/5435), @meitinger)
* ASGI/WSGI apps can now listen on all ports for a specific hostname.
  This makes it simpler to accept both HTTP and HTTPS.
  ([#5725](https://github.com/mitmproxy/mitmproxy/pull/5725), @mhils)
* Add `replay.server.add` command for adding flows to server replay buffer
  ([#5851](https://github.com/mitmproxy/mitmproxy/pull/5851), @italankin)
* Remove string escaping in raw view.
  ([#5470](https://github.com/mitmproxy/mitmproxy/issues/5470), @stephenspol)
* Updating `Request.port` now also updates the Host header if present.
  This aligns with `Request.host`, which already does this.
  ([#5908](https://github.com/mitmproxy/mitmproxy/pull/5908), @sujaldev)
* Fix editing of multipart HTTP requests from the CLI.
  ([#5148](https://github.com/mitmproxy/mitmproxy/issues/5148), @mhils)
* Add documentation on using Magisk module for intercepting traffic in Android production builds.
  ([#5924](https://github.com/mitmproxy/mitmproxy/pull/5924), @Jurrie)
* Fix a bug where the direction indicator in the message stream view would be in the wrong direction.
  ([#5921](https://github.com/mitmproxy/mitmproxy/issues/5921), @konradh)
* Fix a bug where peername would be None in tls_passthrough script, which would make it not working.
  ([#5904](https://github.com/mitmproxy/mitmproxy/pull/5904), @truebit)
* the `esc` key can now be used to exit the current view
  ([#6087](https://github.com/mitmproxy/mitmproxy/pull/6087), @sujaldev)
* focus-follow shortcut will now work in flow view context too.
  ([#6088](https://github.com/mitmproxy/mitmproxy/pull/6088), @sujaldev)
* Fix a bug where a server connection timeout would cause requests to be issued with a wrong SNI in reverse proxy mode.
  ([#6148](https://github.com/mitmproxy/mitmproxy/pull/6148), @mhils)
* The `server_replay_nopop` option has been renamed to `server_replay_reuse` to avoid confusing double-negation.
  ([#6084](https://github.com/mitmproxy/mitmproxy/issues/6084), @prady0t, @Semnodime)
* Add zstd to valid gRPC encoding schemes.
  ([#6188](https://github.com/mitmproxy/mitmproxy/pull/6188), @tsaaristo)
* For reverse proxy directly accessed via IP address, the IP address is now included
  as a subject in the generated certificate.
  ([#6202](https://github.com/mitmproxy/mitmproxy/pull/6202), @mhils)
* Enable legacy SSL connect when connecting to server if the `ssl_insecure` flag is set.
  ([#6281](https://github.com/mitmproxy/mitmproxy/pull/6281), @DurandA)
* Change wording in the [http-reply-from-proxy.py example](https://github.com/mitmproxy/mitmproxy/blob/main/examples/addons/http-reply-from-proxy.py).
  ([#6117](https://github.com/mitmproxy/mitmproxy/pull/6117), @Semnodime)
* Added option to specify an elliptic curve for key exchange between mitmproxy <-> server
  ([#6170](https://github.com/mitmproxy/mitmproxy/pull/6170), @Mike-Ki-ASD)
* Add "Prettier" code linting tool to mitmweb.
  ([#5985](https://github.com/mitmproxy/mitmproxy/pull/5985), @alexgershberg)
* When logging exceptions, provide the entire exception object to log handlers
  ([#6295](https://github.com/mitmproxy/mitmproxy/pull/6295), @mhils)
* mitmproxy now requires Python 3.10 or above.
  ([#5954](https://github.com/mitmproxy/mitmproxy/pull/5954), @mhils)

### Breaking Changes

* The `onboarding_port` option has been removed. The onboarding app now responds
  to all requests for the hostname specified in `onboarding_host`.
* `connection.Client` and `connection.Server` now accept keyword arguments only.
  This is a breaking change for custom addons that use these classes directly.

## 02 November 2022: mitmproxy 9.0.1

* The precompiled binaries now ship with OpenSSL 3.0.7, which resolves CVE-2022-3602 and CVE-2022-3786.
* Performance and stability improvements for WireGuard mode.
  ([#5694](https://github.com/mitmproxy/mitmproxy/issues/5694), @mhils, @decathorpe)
* Fix a bug where the standalone Linux binaries would require libffi to be installed.
  ([#5699](https://github.com/mitmproxy/mitmproxy/issues/5699), @mhils)
* Hard exit when mitmproxy cannot write logs, fixes endless loop when parent process exits.
  ([#4669](https://github.com/mitmproxy/mitmproxy/issues/4669), @Prinzhorn)
* Fix a permission error affecting the Docker images.
  ([#5700](https://github.com/mitmproxy/mitmproxy/issues/5700), @mhils)


## 28 October 2022: mitmproxy 9.0.0

### Major Features

* Add Raw UDP support.
  ([#5414](https://github.com/mitmproxy/mitmproxy/pull/5414), @meitinger)
* Add WireGuard mode to enable transparent proxying via WireGuard.
  ([#5562](https://github.com/mitmproxy/mitmproxy/pull/5562), @decathorpe, @mhils)
* Add DTLS support.
  ([#5397](https://github.com/mitmproxy/mitmproxy/pull/5397), @kckeiks).
* Add a quick help bar to mitmproxy.
  ([#5381](https://github.com/mitmproxy/mitmproxy/pull/5381/), [#5652](https://github.com/mitmproxy/mitmproxy/pull/5652), @kckeiks, @mhils).

### Deprecations

* Deprecate `add_log` event hook. Users should use the builtin `logging` module instead.
  See [the docs](https://docs.mitmproxy.org/dev/addons-api-changelog/) for details and upgrade instructions.
  ([#5590](https://github.com/mitmproxy/mitmproxy/pull/5590), @mhils)
* Deprecate `mitmproxy.ctx.log` in favor of Python's builtin `logging` module.
  See [the docs](https://docs.mitmproxy.org/dev/addons-api-changelog/) for details and upgrade instructions.
  ([#5590](https://github.com/mitmproxy/mitmproxy/pull/5590), @mhils)

### Breaking Changes

 * The `mode` option is now a list of server specs instead of a single spec.
   The CLI interface is unaffected, but users may need to update their `config.yaml`.
   ([#5393](https://github.com/mitmproxy/mitmproxy/pull/5393), @mhils)

### Full Changelog

* Mitmproxy binaries now ship with Python 3.11.
  ([#5678](https://github.com/mitmproxy/mitmproxy/issues/5678), @mhils)
* One mitmproxy instance can now spawn multiple proxy servers.
  ([#5393](https://github.com/mitmproxy/mitmproxy/pull/5393), @mhils)
* Add syntax highlighting to JSON and msgpack content view.
  ([#5623](https://github.com/mitmproxy/mitmproxy/issues/5623), @SapiensAnatis)
* Add MQTT content view.
  ([#5588](https://github.com/mitmproxy/mitmproxy/pull/5588), @nikitastupin, @abbbe)
* Setting `connection_strategy` to `lazy` now also disables early
  upstream connections to fetch TLS certificate details.
  ([#5487](https://github.com/mitmproxy/mitmproxy/pull/5487), @mhils)
* Fix order of event hooks on startup.
  ([#5376](https://github.com/mitmproxy/mitmproxy/issues/5376), @meitinger)
* Include server information in bind/listen errors.
  ([#5495](https://github.com/mitmproxy/mitmproxy/pull/5495), @meitinger)
* Include information about lazy connection_strategy in related errors.
  ([#5465](https://github.com/mitmproxy/mitmproxy/pull/5465), @meitinger, @mhils)
* Fix `tls_version_server_min` and `tls_version_server_max` options.
  ([#5546](https://github.com/mitmproxy/mitmproxy/issues/5546), @mhils)
* Added Magisk module generation for Android onboarding.
  ([#5547](https://github.com/mitmproxy/mitmproxy/pull/5547), @jorants)
* Update Linux binary builder to Ubuntu 20.04, bumping the minimum glibc version to 2.31.
  ([#5547](https://github.com/mitmproxy/mitmproxy/pull/5547), @jorants)
* Add "Save filtered" button in mitmweb.
  ([#5531](https://github.com/mitmproxy/mitmproxy/pull/5531), @rnbwdsh, @mhils)
* Render application/prpc content as gRPC/Protocol Buffers
  ([#5568](https://github.com/mitmproxy/mitmproxy/pull/5568), @selfisekai)
* Mitmweb now supports `content_view_lines_cutoff`.
  ([#5548](https://github.com/mitmproxy/mitmproxy/pull/5548), @sanlengjingvv)
* Fix a mitmweb crash when scrolling down the flow list.
  ([#5507](https://github.com/mitmproxy/mitmproxy/pull/5507), @LIU-shuyi)
* Add HTTP/3 binary frame content view.
  ([#5582](https://github.com/mitmproxy/mitmproxy/pull/5582), @mhils)
* Fix mitmweb not properly opening a browser and being stuck on some Linux.
  ([#5522](https://github.com/mitmproxy/mitmproxy/issues/5522), @Prinzhorn)
* Fix race condition when updating mitmweb WebSocket connections that are closing.
  ([#5405](https://github.com/mitmproxy/mitmproxy/issues/5405), [#5686](https://github.com/mitmproxy/mitmproxy/issues/5686), @mhils)
* Fix mitmweb crash when using filters.
  ([#5658](https://github.com/mitmproxy/mitmproxy/issues/5658), [#5661](https://github.com/mitmproxy/mitmproxy/issues/5661), @LIU-shuyi, @mhils)
* Fix missing default port when starting a browser.
  ([#5687](https://github.com/mitmproxy/mitmproxy/issues/5687), @rbdixon)
* Add docs for transparent mode on Windows.
  ([#5402](https://github.com/mitmproxy/mitmproxy/issues/5402), @stephenspol)

## 28 June 2022: mitmproxy 8.1.1

* Support specifying the local address for outgoing connections
  ([#5364](https://github.com/mitmproxy/mitmproxy/discussions/5364), @meitinger)
* Fix a bug where an excess empty chunk has been sent for chunked HEAD request.
  ([#5372](https://github.com/mitmproxy/mitmproxy/discussions/5372), @jixunmoe)
* Drop pkg_resources dependency.
  ([#5401](https://github.com/mitmproxy/mitmproxy/issues/5401), @PavelICS)
* Fix huge (>65kb) http2 responses corrupted.
  ([#5428](https://github.com/mitmproxy/mitmproxy/issues/5428), @dhabensky)
* Remove overambitious assertions in the HTTP state machine,
  fix some error handling.
  ([#5383](https://github.com/mitmproxy/mitmproxy/issues/5383), @mhils)
* Use default_factory for parser_options.
  ([#5474](https://github.com/mitmproxy/mitmproxy/issues/5474), @rathann)

## 15 May 2022: mitmproxy 8.1.0

* DNS support
  ([#5232](https://github.com/mitmproxy/mitmproxy/pull/5232), @meitinger)
* Mitmproxy now requires Python 3.9 or above.
  ([#5233](https://github.com/mitmproxy/mitmproxy/issues/5233), @mhils)
* Fix a memory leak in mitmdump where flows were kept in memory.
  ([#4786](https://github.com/mitmproxy/mitmproxy/issues/4786), @mhils)
* Replayed flows retain their current position in the flow list.
  ([#5227](https://github.com/mitmproxy/mitmproxy/issues/5227), @mhils)
* Periodically send HTTP/2 ping frames to keep connections alive.
  ([#5046](https://github.com/mitmproxy/mitmproxy/issues/5046), @EndUser509)
* Console Performance Improvements
  ([#3427](https://github.com/mitmproxy/mitmproxy/issues/3427), @BkPHcgQL3V)
* Warn users if server side event responses are received without streaming.
  ([#4469](https://github.com/mitmproxy/mitmproxy/issues/4469), @mhils)
* Add flatpak support to the browser addon
  ([#5200](https://github.com/mitmproxy/mitmproxy/issues/5200), @pauloromeira)
* Add example addon to dump contents to files based on a filter expression
  ([#5190](https://github.com/mitmproxy/mitmproxy/issues/5190), @redraw)
* Fix a bug where the wrong SNI is sent to an upstream HTTPS proxy
  ([#5109](https://github.com/mitmproxy/mitmproxy/issues/5109), @mhils)
* Make sure that mitmproxy displays error messages on startup.
  ([#5225](https://github.com/mitmproxy/mitmproxy/issues/5225), @mhils)
* Add example addon for domain fronting.
  ([#5217](https://github.com/mitmproxy/mitmproxy/issues/5217), @randomstuff)
* Improve cut addon to better handle binary contents
  ([#3965](https://github.com/mitmproxy/mitmproxy/issues/3965), @mhils)
* Fix text truncation for full-width characters
  ([#4278](https://github.com/mitmproxy/mitmproxy/issues/4278), @kjy00302)
* Fix mitmweb export copy failed in non-secure domain.
  ([#5264](https://github.com/mitmproxy/mitmproxy/issues/5264), @Pactortester)
* Add example script for manipulating cookies.
  ([#5278](https://github.com/mitmproxy/mitmproxy/issues/5278), @WillahScott)
* When opening an external viewer for message contents, mailcap files are not considered anymore.
  This preempts the upcoming deprecation of Python's `mailcap` module.
  ([#5297](https://github.com/mitmproxy/mitmproxy/issues/5297), @KORraNpl)
* Fix hostname encoding for IDNA domains in upstream mode.
  ([#5316](https://github.com/mitmproxy/mitmproxy/issues/5316), @nneonneo)
* Fix hot reloading of contentviews.
  ([#5319](https://github.com/mitmproxy/mitmproxy/issues/5319), @nneonneo)
* Ignore HTTP/2 information responses instead of raising an error.
  ([#5332](https://github.com/mitmproxy/mitmproxy/issues/5332), @mhils)
* Improve performance and memory usage by reusing OpenSSL contexts.
  ([#5339](https://github.com/mitmproxy/mitmproxy/issues/5339), @mhils)
* Fix handling of multiple Cookie headers when proxying HTTP/2 to HTTP/1
  ([#5337](https://github.com/mitmproxy/mitmproxy/issues/5337), @rinsuki)
* Improve http_manipulate_cookies.py example.
  ([#5578](https://github.com/mitmproxy/mitmproxy/issues/5578), @insilications)

## 19 March 2022: mitmproxy 8.0.0

### Major Changes

* Major improvements to the web interface (@gorogoroumaru)
* Event hooks can now be async (@nneonneo, [#5106](https://github.com/mitmproxy/mitmproxy/issues/5106))
* New [`tls_{established,failed}_{client,server}` event hooks](https://docs.mitmproxy.org/dev/api/events.html#TLSEvents)
  to record negotiation success/failure (@mhils, [#4790](https://github.com/mitmproxy/mitmproxy/pull/4790))

### Security Fixes

* [CVE-2022-24766](https://github.com/mitmproxy/mitmproxy/security/advisories/GHSA-gcx2-gvj7-pxv3):
  Fix request smuggling vulnerability reported by @zeyu2001 (@mhils)

### Full Changelog

* Support proxy authentication for SOCKS v5 mode (@starplanet)
* Make it possible to ignore connections in the tls_clienthello event hook (@mhils)
* fix some responses not being decoded properly if the encoding was uppercase (#4735, @Mattwmaster58)
* Trigger event hooks for flows with semantically invalid requests, for example invalid content-length headers (@mhils)
* Improve error message on TLS version mismatch (@mhils)
* Windows: Switch to Python's default asyncio event loop, which increases the number of sockets
  that can be processed simultaneously (@mhils)
* Add `client_replay_concurrency` option, which allows more than one client replay request to be in-flight at a time. (@rbdixon)
* New content view which handles gRPC/protobuf. Allows to apply custom definitions to visualize different field decodings.
  Includes example addon which applies custom definitions for selected gRPC traffic (@mame82)
* Fix a crash caused when editing string option (#4852, @rbdixon)
* Base container image bumped to Debian 11 Bullseye (@Kriechi)
* Upstream replays don't do CONNECT on plaintext HTTP requests (#4876, @HoffmannP)
* Remove workarounds for old pyOpenSSL versions (#4831, @KarlParkinson)
* Add fonts to asset filter (~a) (#4928, @elespike)
* Fix bug that crashed when using `view.flows.resolve` (#4916, @rbdixon)
* Fix a bug where `running()` is invoked twice on startup (#3584, @mhils)
* Correct documentation example for User-Agent header modification (#4997, @jamesyale)
* Fix random connection stalls (#5040, @EndUser509)
* Add `n` new flow keybind to mitmweb (#5061, @ianklatzco)
* Fix compatibility with BoringSSL (@pmoulton)
* Added `WebSocketMessage.injected` flag (@Prinzhorn)
* Add example addon for saving streamed data to individual files (@EndUser509)
* Change connection event hooks to be blocking.
  Processing will only resume once the event hook has finished. (@Prinzhorn)
* Reintroduce `Flow.live`, which signals if a flow belongs to a currently active connection. (#4207, @mhils)
* Speculative fix for some rare HTTP/2 connection stalls (#5158, @EndUser509)
* Add ability to specify custom ports with LDAP authentication (#5068, @demonoidvk)
* Add support for rotating saved streams every hour or day (@EndUser509)
* Console Improvements on Windows (@mhils)
* Fix processing of `--set` options (#5067, @marwinxxii)
* Lowercase user-added header names and emit a log message to notify the user when using HTTP/2 (#4746, @mhils)
* Exit early if there are errors on startup (#4544, @mhils)
* Fixed encoding guessing: only search for meta tags in HTML bodies (##4566, @Prinzhorn)
* Binaries are now built with Python 3.10 (@mhils)

## 28 September 2021: mitmproxy 7.0.4

* Do not add a Content-Length header for chunked HTTP/1 messages (@matthewhughes934)

## 16 September 2021: mitmproxy 7.0.3

* [CVE-2021-39214](https://github.com/mitmproxy/mitmproxy/security/advisories/GHSA-22gh-3r9q-xf38):
  Fix request smuggling vulnerabilities reported by @chinchila (@mhils)
* Expose TLS 1.0 as possible minimum version on older pyOpenSSL releases (@mhils)
* Fix compatibility with Python 3.10 (@mhils)

## 4 August 2021: mitmproxy 7.0.2

* Fix a WebSocket crash introduced in 7.0.1 (@mhils)

## 3 August 2021: mitmproxy 7.0.1

* Performance: Re-use OpenSSL contexts to enable TLS session resumption (@mhils)
* Disable HTTP/2 CONNECT for Secure Web Proxies to fix compatibility with Firefox (@mhils)
* Use local IP address as certificate subject if no other info is available (@mhils)
* Make it possible to return multiple chunks for HTTP stream modification (@mhils)
* Don't send WebSocket CONTINUATION frames when the peer does not send any (@Pilphe)
* Fix HTTP stream modify example. (@mhils)
* Fix a crash caused by no-op assignments to `Server.address` (@SaladDais)
* Fix a crash when encountering invalid certificates (@mhils)
* Fix a crash when pressing the Home/End keys in some screens (@rbdixon)
* Fix a crash when reading corrupted flow dumps (@mhils)
* Fix multiple crashes on flow export (@mhils)
* Fix a bug where ASGI apps did not see the request body (@mhils)
* Minor documentation improvements (@mhils)

## 16 July 2021: mitmproxy 7.0

### New Proxy Core (@mhils, [blog post](https://www.mitmproxy.org/posts/releases/mitmproxy7/))

Mitmproxy has a completely new proxy core, fixing many longstanding issues:

* **Secure Web Proxy:** Mitmproxy now supports TLS-over-TLS to already encrypt the connection to the proxy.
* **Server-Side Greetings:** Mitmproxy now supports proxying raw TCP connections, including ones that start
  with a server-side greeting (e.g. SMTP).
* **HTTP/1 – HTTP/2 Interoperability:** mitmproxy can now accept an HTTP/2 connection from the client,
  and forward it to an HTTP/1 server.
* **HTTP/2 Redirects:** The request destination can now be changed on HTTP/2 flows.
* **Connection Strategy:** Users can now specify if they want mitmproxy to eagerly connect upstream
  or wait as long as possible. Eager connections are required to detect protocols with server-side
  greetings, lazy connections enable the replay of responses without connecting to an upstream server.
* **Timeout Handling:** Mitmproxy will now clean up idle connections and also abort requests if the client disconnects
  in the meantime.
* **Host Header-based Proxying:** If the request destination is unknown, mitmproxy now falls back to proxying
  based on the Host header. This means that requests can often be redirected to mitmproxy using
  DNS spoofing only.
* **Internals:** All protocol logic is now separated from I/O (["sans-io"](https://sans-io.readthedocs.io/)).
  This greatly improves testing capabilities, prevents a wide array of race conditions, and increases
  proper isolation between layers.

### Additional Changes

* mitmproxy's command line interface now supports Windows (@mhils)
* The `clientconnect`, `clientdisconnect`, `serverconnect`, `serverdisconnect`, and `log`
  events have been replaced with new events, see addon documentation for details (@mhils)
* Contentviews now implement `render_priority` instead of `should_render`, allowing more specialization (@mhils)
* Addition of block_list option to block requests with a set status code (@ericbeland)
* Make mitmweb columns configurable and customizable (@gorogoroumaru)
* Automatic JSON view mode when `+json` suffix in content type (@kam800)
* Use pyca/cryptography to generate certificates, not pyOpenSSL (@mhils)
* Remove the legacy protocol stack (@Kriechi)
* Remove all deprecated pathod and pathoc tools and modules (@Kriechi)
* In reverse proxy mode, mitmproxy now does not assume TLS if no scheme
  is given but a custom port is provided (@mhils)
* Remove the following options: `http2_priority`, `relax_http_form_validation`, `upstream_bind_address`,
  `spoof_source_address`, and `stream_websockets`. If you depended on one of them please let us know.
  mitmproxy never phones home, which means we don't know how prominently these options were used. (@mhils)
* Fix IDNA host 'Bad HTTP request line' error (@grahamrobbins)
* Pressing `?` now exits console help view (@abitrolly)
* `--modify-headers` now works correctly when modifying a header that is also part of the filter expression (@Prinzhorn)
* Fix SNI-related reproducibility issues when exporting to curl/httpie commands. (@dkasak)
* Add option `export_preserve_original_ip` to force exported command to connect to IP from original request.
  Only supports curl at the moment. (@dkasak)
* Major proxy protocol testing (@r00t-)
* Switch Docker image release to be based on Debian (@PeterDaveHello)
* Multiple Browsers: The `browser.start` command may be executed more than once to start additional
  browser sessions. (@rbdixon)
* Improve readability of SHA256 fingerprint. (@wrekone)
* Metadata and Replay Flow Filters: Flows may be filtered based on metadata and replay status. (@rbdixon)
* Flow control: don't read connection data faster than it can be forwarded. (@hazcod)
* Docker images for ARM64 architecture (@hazcod, @mhils)
* Fix parsing of certificate issuer/subject with escaped special characters (@Prinzhorn)
* Customize markers with emoji, and filters: The `flow.mark` command may be used to mark a flow with either the default
  "red ball" marker, a single character, or an emoji like `:grapes:`. Use the `~marker` filter to filter on marker
  characters. (@rbdixon)
* New `flow.comment` command to add a comment to the flow. Add `~comment <regex>` filter syntax to search flow comments.
  (@rbdixon)
* Fix multipart forms losing `boundary` values on edit. (@roytu)
* `Transfer-Encoding: chunked` HTTP message bodies are now retained if they are below the stream_large_bodies limit.
  (@mhils)
* `json()` method for HTTP Request and Response instances will return decoded JSON body. (@rbdixon)
* Support for HTTP/2 Push Promises has been dropped. (@mhils)
* Make it possible to set sequence options from the command line. (@Yopi)

## 15 December 2020: mitmproxy 6.0.2

* Fix reading of saved flows in mitmweb.

## 13 December 2020: mitmproxy 6.0.1

* Fix flow serialization in mitmweb.

## 13 December 2020: mitmproxy 6.0

* Mitmproxy now requires Python 3.8 or above.
* Deprecation of pathod and pathoc tools and modules. Future releases will not contain them! (@Kriechi)
* SSLKEYLOGFILE now supports TLS 1.3 secrets (@mhils)
* Fix query parameters in asgiapp addon (@jpstotz)
* Fix command history failing on file I/O errors (@Kriechi)
* Add example addon to suppress unwanted error messages sent by mitmproxy. (@anneborcherding)
* Updated imports and styles for web scanner helper addons. (@anneborcherding)
* Inform when underscore-formatted options are used in client arg. (@jrblixt)
* ASGIApp now ignores loaded HTTP flows from somewhere. (@linw1995)
* Binaries are now built with Python 3.9 (@mhils)
* Fixed the web UI showing blank page on clicking details tab when server address is missing (@samhita-sopho)
* Tests: Replace asynctest with stdlib mock (@felixonmars)
* MapLocal now keeps its configuration when other options are set. (@mhils)
* Host headers with non-standard ports are now properly updated in reverse proxy mode. (@mhils)
* Fix missing host header when replaying HTTP/2 flows (@Granitosaurus)

## 01 November 2020: mitmproxy 5.3

### Full Changelog

* Support for Python 3.9 (@mhils)
* Add MsgPack content viewer (@tasn)
* Use `@charset` to decode CSS files if available (@Prinzhorn)
* Fix links to anticache docs in mitmweb and use HTTPS for links to documentation (@rugk)
* Updated typing for WebsocketMessage.content (@Prinzhorn)
* Add option `console_strip_trailing_newlines`, and no longer strip trailing newlines by default (@capt8bit)
* Prevent transparent mode from connecting to itself in the basic cases (@Prinzhorn)
* Display HTTP trailers in mitmweb (@sanlengjingvv)
* Revamp onboarding app (@mhils)
* Add ASGI support for embedded apps (@mhils)
* Updated raw exports to not remove headers (@wchasekelley)
* Fix file unlinking before external viewer finishes loading (@wchasekelley)
* Add --cert-passphrase command line argument (@mirosyn)
* Add interactive tutorials to the documentation (@mplattner)
* Support `deflateRaw` for `Content-Encoding`'s (@kjoconnor)
* Fix broken requests without body on HTTP/2 (@Kriechi)
* Add support for sending (but not parsing) HTTP Trailers to the HTTP/1.1 protocol (@bburky)
* Add support to echo http trailers in dumper addon (@shiv6146)
* Fix OpenSSL requiring different CN for root and leaf certificates (@mhils)
* ... and various other fixes, documentation improvements, dependency version bumps, etc.

## 18 July 2020: mitmproxy 5.2

* Add Filter message to mitmdump (@sarthak212)
* Display TCP flows at flow list (@Jessonsotoventura, @nikitastupin, @mhils)
* Colorize JSON Contentview (@sarthak212)
* Fix console crash when entering regex escape character in half-open string (@sarthak212)
* Integrate contentviews to TCP flow details (@nikitastupin)
* Added add-ons that enhance the performance of web application scanners (@anneborcherding)
* Increase WebSocket message timestamp precision (@JustAnotherArchivist)
* Fix HTTP reason value on HTTP/2 reponses (@rbdixon)
* mitmweb: support wslview to open a web browser (@G-Rath)
* Fix dev version detection with parent git repo (@JustAnotherArchivist)
* Restructure examples and supported addons (@mhils)
* Certificate generation: mark SAN as critical if no CN is set (@mhils)
* Simplify Replacements with new ModifyBody addon (@mplattner)
* Rename SetHeaders addon to ModifyHeaders (@mplattner)
* mitmweb: "New -> File" menu option has been renamed to "Clear All" (@yogeshojha)
* Add new MapRemote addon to rewrite URLs of requests (@mplattner)
* Add support for HTTP Trailers to the HTTP/2 protocol (@sanlengjingvv and @Kriechi)
* Fix certificate runtime error during expire cleanup (@gorogoroumaru)
* Fixed the DNS Rebind Protection for secure support of IPv6 addresses (@tunnelpr0)
* WebSockets: match the HTTP-WebSocket flow for the ~websocket filter (@Kriechi)
* Fix deadlock caused by the "replay.client.stop" command (@gorogoroumaru)
* Add new MapLocal addon to serve local files instead of remote resources (@mplattner and @mhils)
* Add minimal TCP interception and modification (@nikitastupin)
* Add new CheckSSLPinning addon to check SSL-Pinning on client (@su-vikas)
* Add a JSON dump script: write data into a file or send to an endpoint as JSON (@emedvedev)
* Fix console output formatting (@sarthak212)
* Add example for proxy authentication using selenium (@anneborcherding and @weichweich)

## 13 April 2020: mitmproxy 5.1.1

* Fixed Docker images not starting due to missing shell

## 13 April 2020: mitmproxy 5.1

### Major Changes

* Initial Support for TLS 1.3

### Full Changelog

* Reduce leaf certificate validity to one year due to upcoming browser changes (@mhils)
* Rename mitmweb's `web_iface` option to `web_host` for consistency (@oxr463)
* Sending a SIGTERM now exits mitmproxy without prompt, SIGINT still asks (@ThinkChaos)
* Don't force host header on outgoing requests (@mhils)
* Additional documentation and examples for WebSockets (@Kriechi)
* Gracefully handle hyphens in domain names (@matosconsulting)
* Fix header replacement count (@naivekun)
* Emit serverconnect event only after a connection has been established (@Prinzhorn)
* Fix ValueError in table mode of server replay flow (@ylmrx)
* HTTP/2: send all stream reset types to other connection (@rohfle)
* HTTP/2: fix WINDOW_UPDATE swallowed on closed streams (@Kriechi)
* Fix wrong behavior of --allow-hosts options (@BlownSnail)
* Additional and updated documentation for examples, WebSockets, Getting Started (@Kriechi)

## 27 December 2019: mitmproxy 5.0.1

* Fixed precompiled Linux binaries to not crash in table mode
* Display webp images in mitmweb (@cixtor)

## 16 December 2019: mitmproxy 5.0

### Major Changes

* Added new Table UI (@Jessonsotoventura)
* Added EKU extension to certificates. This fixes support for macOS Catalina (@vin01)

### Security Fixes

* Fixed command injection vulnerabilities when exporting flows as curl/httpie commands (@cript0nauta)
* Do not echo unsanitized user input in HTTP error responses (@fimad)

### Full Changelog

* Moved to GitHub CI for Continuous Integration, dropping support for old Linux and macOS releases. (#3728)
* Vastly improved command parsing, in particular for setting flow filters (@typoon)
* Added a new flow export for raw responses (@mckeimic)
* URLs are now edited in an external editor (@Jessonsotoventura)
* mitmproxy now has a command history (@typoon)
* Added terminal like keyboard shortcuts for the command bar (ctrl+w, ctrl+a, ctrl+f, ...) (@typoon)
* Fixed issue with improper handling of non-ascii characters in URLs (@rjt-gupta)
* Filtering can now use unicode characters (@rjt-gupta)
* Fixed issue with user keybindings not being able to override default keybindings
* Improved installation instructions
* Added support for IPV6-only environments (@sethb157)
* Fixed bug with server replay (@rjt-gupta)
* Fixed issue with duplicate error responses (@ccssrryy)
* Users can now set a specific external editor using $MITMPROXY_EDITOR (@rjt-gupta)
* Config file can now be called `config.yml` or `config.yaml` (@ylmrx)
* Fixed crash on `view.focus.[next|prev]` (@ylmrx)
* Updated documentation to help using mitmproxy certificate on Android (@jannst)
* Added support to parse IPv6 entries from `pfctl` on MacOS. (@tomlabaude)
* Fixed instructions on how to build the documentation (@jannst)
* Added a new `--allow-hosts` option (@pierlon)
* Added support for zstd content-encoding (@tsaaristo)
* Fixed issue where the replay server would corrupt the Date header (@tonyb486)
* Improve speed for WebSocket interception (@MathieuBordere)
* Fixed issue with parsing JPEG files. (@lusceu)
* Improve example code style (@BoboTiG)
* Fixed issue converting void responses to HAR (@worldmind)
* Color coded http status codes in mitmweb (@arun-94)
* Added organization to generated certificates (@Abcdefghijklmnopqrstuvwxyzxyz)
* Errors are now displayed on sys.stderr (@JessicaFavin)
* Fixed issue with replay timestamps (@rjt-gupta)
* Fixed copying in mitmweb on macOS (@XZzYassin)

## 31 July 2018: mitmproxy 4.0.4

* Security: Protect mitmweb against DNS rebinding. (CVE-2018-14505, @atx)
* Reduce certificate lifetime to two years to be conformant with
  the current CA/Browser Forum Baseline Requirements. (@muffl0n)
  (https://cabforum.org/2017/03/17/ballot-193-825-day-certificate-lifetimes/)
* Update cryptography to version 2.3.

## 15 June 2018: mitmproxy 4.0.3

* Add support for IPv6 transparent mode on Windows (#3174)
* Add Docker images for ARMv7 - Raspberry Pi (#3190)
* Major overhaul of our release workflow - you probably won't notice it, but for us it's a big thing!
* Fix the Python version detection on Python 3.5, we now show a more intuitive error message (#3188)
* Fix application shutdown on Windows (#3172)
* Fix IPv6 scope suffixes in block addon (#3164)
* Fix options update when added (#3157)
* Fix "Edit Flow" button in mitmweb (#3136)

## 15 June 2018: mitmproxy 4.0.2

* Skipped!

## 17 May 2018: mitmproxy 4.0.1

### Bugfixes

* The previous release had a packaging issue, so we bumped it to v4.0.1 and re-released it.
* This contains no actual bugfixes or new features.

## 17 May 2018: mitmproxy 4.0

### Features

* mitmproxy now requires Python 3.6!
* Moved the core to asyncio - which gives us a very significant performance boost!
* Reduce memory consumption by using `SO_KEEPALIVE` (#3076)
* Export request as httpie command (#3031)
* Configure mitmproxy console keybindings with the keys.yaml file. See docs for more.

### Breaking Changes

* The --conf command-line flag is now --confdir, and specifies the mitmproxy configuration
    directory, instead of the options yaml file (which is at `config.yaml` under the configuration directory).
* `allow_remote` got replaced by `block_global` and `block_private` (#3100)
* No more custom events (#3093)
* The `cadir` option has been renamed to `confdir`
* We no longer magically capture print statements in addons and translate
    them to logs. Please use `ctx.log.info` explicitly.

### Bugfixes

* Correctly block connections from remote clients with IPv4-mapped IPv6 client addresses (#3099)
* Expand `~` in paths during the `cut` command (#3078)
* Remove socket listen backlog constraint
* Improve handling of user script exceptions (#3050, #2837)
* Ignore signal errors on windows
* Fix traceback for commands with un-terminated escape characters (#2810)
* Fix request replay when proxy is bound to local interface (#2647)
* Fix traceback when running scripts on a flow twice (#2838)
* Fix traceback when killing intercepted flow (#2879)
* And lots of typos, docs improvements, revamped examples, and general fixes!

## 05 April 2018: mitmproxy 3.0.4

* Fix an issue that caused mitmproxy to not retry HTTP requests on timeout.
* Various other fixes (@kira0204, @fenilgandhi, @tran-tien-dat, @smonami,
  @luzpaz, @fristonio, @kajojify, @Oliver-Fish, @hcbarry, @jplochocki, @MikeShi42,
  @ghillu, @emilstahl)

## 25 February 2018: mitmproxy 3.0.3

* Fix an issue that caused mitmproxy to lose keyboard control after spawning an external editor.

## 23 February 2018: mitmproxy 3.0.1

* Fix a quote-related issue affecting the mitmproxy console command prompt.

## 22 February 2018: mitmproxy 3.0

### Major Changes

* Commands: A consistent, typed mechanism that allows addons to expose actions
  to users.
* Options: A typed settings store for use by mitmproxy and addons.
* Shift most of mitmproxy's own functionality into addons.
* Major improvements to mitmproxy console, including an almost complete
  rewrite of the user interface, integration of commands, key bindings, and
  multi-pane layouts.
* Major Improvements to mitmproxy’s web interface, mitmweb. (Matthew Shao,
  Google Summer of Code 2017)
* Major Improvements to mitmproxy’s content views and protocol layers (Ujjwal
  Verma, Google Summer of Code 2017)
* Faster JavaScript and CSS beautifiers. (Ujjwal Verma)

### Minor Changes

* Vastly improved JavaScript test coverage (Matthew Shao)
* Options editor for mitmweb (Matthew Shao)
* Static web-based flow viewer (Matthew Shao)
* Request streaming for HTTP/1.x and HTTP/2 (Ujjwal Verma)
* Implement more robust content views using Kaitai Struct (Ujjwal Verma)
* Protobuf decoding now works without protoc being installed on the host
  system (Ujjwal Verma)
* PNG, GIF, and JPEG can now be parsed without Pillow, which simplifies
  mitmproxy installation and moves parsing from unsafe C to pure Python (Ujjwal Verma)
* Add parser for ICO files (Ujjwal Verma)
* Migrate WebSockets implementation to wsproto. This reduces code size and
  adds WebSocket compression support. (Ujjwal Verma)
* Add “split view” to split mitmproxy’s UI into two separate panes.
* Add key binding viewer and editor
* Add a command to spawn a preconfigured Chrome browser instance from
  mitmproxy
* Fully support mitmproxy under the Windows Subsystem for Linux (WSL), work
  around display errors
* Add XSS scanner addon (@ddworken)
* Add ability to toggle interception (@mattweidner)
* Numerous documentation improvements (@pauloromeira, @rst0git, @rgerganov,
  @fulldecent, @zhigang1992, @F1ashhimself, @vinaydargar, @jonathanrfisher1,
  @BasThomas, @LuD1161, @ayamamori, @TomTasche)
* Add filters for websocket flows (@s4chin)
* Make it possible to create a response to CONNECT requests in http_connect
  (@mengbiping)
* Redirect stdout in scripts to ctx.log.warn (@nikofil)
* Fix a crash when clearing the event log (@krsoninikhil)
* Store the generated certificate for each flow (@dlenski)
* Add --keep-host-header to retain the host header in reverse proxy mode
  (@krsoninikhil)
* Fix setting palette options (@JordanLoehr)
* Fix a crash with brotli encoding (@whackashoe)
* Provide certificate installation instructions on mitm.it (@ritiek)
* Fix a bug where we did not properly fall back to IPv4 when IPv6 is unavailable (@titeuf87)
* Fix transparent mode on IPv6-enabled macOS systems (@Ga-ryo)
* Fix handling of HTTP messages with multiple Content-Length headers (@surajt97)
* Fix IPv6 authority form parsing in CONNECT requests (@r1b)
* Fix event log display in mitmweb (@syahn)
* Remove private key from PKCS12 file in ~/.mitmproxy (@ograff).
* Add LDAP as a proxy authentication backend (@charlesdhdt)
* Use mypy to check the whole codebase (@iharsh234)
* Fix a crash when duplicating flows (@iharsh234)
* Fix testsuite when the path contains a “.” (@felixonmars)
* Store proxy authentication with flows (@lymanZerga11)
* Match ~d and ~u filters against pretty_host (@dequis)
* Update WBXML content view (@davidpshaw)
* Handle HEAD requests for mitm.it to support Chrome in transparent mode on
  iOS (@tomlabaude)
* Update dns spoofing example to use --keep-host-header (@krsoninikhil)
* Call error handler on HTTPException (@tarnacious)
* Make it possible to remove TLS from upstream HTTP connections
* Update to pyOpenSSL 17.5, cryptography 2.1.4, and OpenSSL 1.1.0g
* Make it possible to retroactively increase log verbosity.
* Make logging from addons thread-safe
* Tolerate imports in user scripts that match hook names
  (`from mitmproxy import log`)
* Update mitmweb to React 16, which brings performance improvements
* Fix a bug where reverting duplicated flows crashes mitmproxy
* Fix a bug where successive requests are sent to the wrong host after a
  request has been redirected.
* Fix a bug that binds outgoing connections to the wrong interface
* Fix a bug where custom certificates are ignored in reverse proxy mode
* Fix import of flows that have been created with mitmproxy 0.17
* Fix formatting of (IPv6) IP addresses in a number of places
* Fix replay for HTTP/2 flows
* Decouple mitmproxy version and flow file format version
* Fix a bug where “mitmdump -nr” does not exit automatically
* Fix a crash when exporting flows to curl
* Fix formatting of sticky cookies
* Improve script reloading reliability by polling the filesystem instead of using watchdog
* Fix a crash when refreshing Set-Cookie headers
* Add connection indicator to mitmweb to alert users when the proxy server stops running
* Add support for certificates with cyrillic domains
* Simplify output of mitmproxy --version
* Add Request.make to simplify request creation in scripts
* Pathoc: Include a host header on CONNECT requests
* Remove HTML outline contentview (#2572)
* Remove Python and Locust export (#2465)
* Remove emojis from tox.ini because flake8 cannot parse that. :(

## 28 April 2017: mitmproxy 2.0.2

* Fix mitmweb's Content-Security-Policy to work with Chrome 58+
* HTTP/2: actually use header normalization from hyper-h2

## 15 March 2017: mitmproxy 2.0.1

* bump cryptography dependency
* bump pyparsing dependency
* HTTP/2: use header normalization from hyper-h2

## 21 February 2017: mitmproxy 2.0

* HTTP/2 is now enabled by default.
* Image ContentView: Parse images with Kaitai Struct (kaitai.io) instead of Pillow.
  This simplifies installation, reduces binary size, and allows parsing in pure Python.
* Web: Add missing flow filters.
* Add transparent proxy support for OpenBSD.
* Check the mitmproxy CA for expiration and warn the user to regenerate it if necessary.
* Testing: Tremendous improvements, enforced 100% coverage for large parts of the
  codebase, increased overall coverage.
* Enforce individual coverage: one source file -> one test file with 100% coverage.
* A myriad of other small improvements throughout the project.
* Numerous bugfixes.

## 26 December 2016: mitmproxy 1.0

* All mitmproxy tools are now Python 3 only! We plan to support Python 3.5 and higher.
* Web-Based User Interface: Mitmproxy now officially has a web-based user interface
  called mitmweb. We consider it stable for all features currently exposed
  in the UI, but it still misses a lot of mitmproxy’s options.
* Windows Compatibility: With mitmweb, mitmproxy is now usable on Windows.
  We are also introducing an installer (kindly sponsored by BitRock) that
  simplifies setup.
* Configuration: The config file format is now a single YAML file. In most cases,
  converting to the new format should be trivial - please see the docs for
  more information.
* Console: Significant UI improvements - including sorting of flows by
  size, type and url, status bar improvements, much faster indentation for
  HTTP views, and more.
* HTTP/2: Significant improvements, but is temporarily disabled by default
  due to wide-spread protocol implementation errors on some large website
* WebSocket: The protocol implementation is now mature, and is enabled by
  default. Complete UI support is coming in the next release. Hooks for
  message interception and manipulation are available.
* A myriad of other small improvements throughout the project.

## 16 October 2016: mitmproxy 0.18

* Python 3 Compatibility for mitmproxy and pathod (Shadab Zafar, GSoC 2016)
* Major improvements to mitmweb (Clemens Brunner & Jason Hao, GSoC 2016)
* Internal Core Refactor: Separation of most features into isolated Addons
* Initial Support for WebSockets
* Improved HTTP/2 Support
* Reverse Proxy Mode now automatically adjusts host headers and TLS Server Name Indication
* Improved HAR export
* Improved export functionality for curl, python code, raw http etc.
* Flow URLs are now truncated in the console for better visibility
* New filters for TCP, HTTP and marked flows.
* Mitmproxy now handles comma-separated Cookie headers
* Merge mitmproxy and pathod documentation
* Mitmdump now sanitizes its console output to not include control characters
* Improved message body handling for HTTP messages:
  `.raw_content` provides the message body as seen on the wire
  `.content` provides the decompressed body (e.g. un-gzipped)
  `.text` provides the body decompressed and decoded body
* New HTTP Message getters/setters for cookies and form contents.
* Add ability to view only marked flows in mitmproxy
* Improved Script Reloader (Always use polling, watch for whole directory)
* Use tox for testing
* Unicode support for tnetstrings
* Add dumpfile converters for mitmproxy versions 0.11 and 0.12
* Numerous bugfixes

## 9 April 2016: mitmproxy 0.17

* Simplify repository and release structure. mitmproxy now comes as a single package, including netlib and pathod.
* Rename the Python package from libmproxy to mitmproxy.
* New option to add server certs to client chain (CVE-2016-2402, John Kozyrakis)
* Enable HTTP/2 by default (Thomas Kriechbaumer)
* Improved HAR extractor (Shadab Zafar)
* Add icon for OSX and Windows binaries
* Add content view for query parameters (Will Coster)
* Initial work on Python 3 compatibility
* locust.io export (Zohar Lorberbaum)
* Fix XSS vulnerability in HTTP errors (Will Coster)
* Numerous bugfixes and minor improvements

## 15 February 2016: mitmproxy 0.16

* Completely revised HTTP2 implementation based on hyper-h2 (Thomas Kriechbaumer)
* Export flows as cURL command, Python code or raw HTTP (Shadab Zafar)
* Fixed compatibility with the Android Emulator (Will Coster)
* Script Reloader: Inline scripts are reloaded automatically if modified (Matthew Shao)
* Inline script hooks for TCP mode (Michael J. Bazzinotti)
* Add default ciphers to support iOS9 App Transport Security (Jorge Villacorta)
* Basic Authentication for mitmweb (Guillem Anguera)
* Exempt connections from interception based on TLS Server Name Indication (David Weinstein)
* Provide Python Wheels for faster installation
* Numerous bugfixes and minor improvements

## 4 December 2015: mitmproxy 0.15

* Support for loading and converting older dumpfile formats (0.13 and up)
* Content views for inline script (@chrisczub)
* Better handling of empty header values (Benjamin Lee/@bltb)
* Fix a gnarly memory leak in mitmdump
* A number of bugfixes and small improvements

## 6 November 2015: mitmproxy 0.14

* Statistics: 399 commits, 13 contributors, 79 closed issues, 37 closed
  PRs, 103 days
* Docs: Greatly updated docs now hosted on ReadTheDocs!
  http://docs.mitmproxy.org
* Docs: Fixed Typos, updated URLs etc. (Nick Badger, Ben Lerner, Choongwoo
  Han, onlywade, Jurriaan Bremer)
* mitmdump: Colorized TTY output
* mitmdump: Use mitmproxy's content views for human-readable output (Chris
  Czub)
* mitmproxy and mitmdump: Support for displaying UTF8 contents
* mitmproxy: add command line switch to disable mouse interaction (Timothy
  Elliott)
* mitmproxy: bug fixes (Choongwoo Han, sethp-jive, FreeArtMan)
* mitmweb: bug fixes (Colin Bendell)
* libmproxy: Add ability to fall back to TCP passthrough for non-HTTP
  connections.
* libmproxy: Avoid double-connect in case of TLS Server Name Indication.
  This yields a massive speedup for TLS handshakes.
* libmproxy: Prevent unnecessary upstream connections (macmantrl)
* Inline Scripts: New API for HTTP Headers:
  http://docs.mitmproxy.org/en/latest/dev/models.html#netlib.http.Headers
* Inline Scripts: Properly handle exceptions in `done` hook
* Inline Scripts: Allow relative imports, provide `__file__`
* Examples: Add probabilistic TLS passthrough as an inline script
* netlib: Refactored HTTP protocol handling code
* netlib: ALPN support
* netlib: fixed a bug in the optional certificate verification.
* netlib: Initial Python 3.5 support (this is the first prerequisite for
  3.x support in mitmproxy)

## 24 July 2015: mitmproxy 0.13

* Upstream certificate validation. See the --verify-upstream-cert,
  --upstream-trusted-confdir and --upstream-trusted-ca parameters. Thanks to
  Kyle Morton (github.com/kyle-m) for his work on this.
* Add HTTP transparent proxy mode. This uses the host headers from HTTP
  traffic (rather than SNI and IP address information from the OS) to
  implement perform transparent proxying. Thanks to github.com/ijiro123 for
  this feature.
* Add ~src and ~dst REGEX filters, allowing matching on source and
  destination addresses in the form of <IP>:<Port>
* mitmproxy console: change g/G keyboard shortcuts to match less. Thanks to
  Jose Luis Honorato (github.com/jlhonora).
* mitmproxy console: Flow marking and unmarking. Marked flows are not
  deleted when the flow list is cleared. Thanks to Jake Drahos
  (github.com/drahosj).
* mitmproxy console: add marking of flows
* Remove the certforward feature. It was added to allow exploitation of
  #gotofail, which is no longer a common vulnerability. Permitting this
  hugely increased the complexity of packaging and distributing mitmproxy.

## 3 June 2015: mitmproxy 0.12.1

* mitmproxy console: mouse interaction - scroll in the flow list, click on
  flow to view, click to switch between tabs.
* Update our crypto defaults: SHA256, 2048 bit RSA, 4096 bit DH parameters.
* BUGFIX: crash under some circumstances when copying to clipboard.
* BUGFIX: occasional crash when deleting flows.

## 18 May 2015: mitmproxy 0.12

* mitmproxy console: Significant revamp of the UI. The major changes are
  listed below, and in addition almost every aspect of the UI has
  been tweaked, and performance has improved significantly.
* mitmproxy console: A new options screen has been created ("o" shortcut),
  and many options that were previously manipulated directly via a
  keybinding have been moved there.
* mitmproxy console: Big improvement in palettes. This includes improvements
  to all colour schemes. Palettes now set the terminal background colour by
  default, and a new --palette-transparent option has been added to disable
  this.
* mitmproxy console: g/G shortcuts throughout mitmproxy console to jump
  to the beginning/end of the current view.
* mitmproxy console: switch  palettes on the fly from the options screen.
* mitmproxy console: A cookie editor has been added for mitmproxy console
  at long last.
* mitmproxy console: Various components of requests and responses can be
  copied to the clipboard from mitmproxy - thanks to @marceloglezer.
* Support for creating new requests from scratch in mitmproxy console (@marceloglezer).
* SSLKEYLOGFILE environment variable to specify a logging location for TLS
  master keys. This can be used with tools like Wireshark to allow TLS
  decoding.
* Server facing SSL cipher suite specification (thanks to Jim Shaver).
* Official support for transparent proxying on FreeBSD - thanks to Mike C
  (http://github.com/mike-pt).
* Many other small bugfixes and improvemenets throughout the project.

## 29 Dec 2014: mitmproxy 0.11.2

* Configuration files - mitmproxy.conf, mitmdump.conf, common.conf in the
  .mitmproxy directory.
* Better handling of servers that reject connections that are not SNI.
* Many other small bugfixes and improvements.

## 15 November 2014: mitmproxy 0.11.1

* Bug fixes: connection leaks some crashes

## 7 November 2014: mitmproxy 0.11

* Performance improvements for mitmproxy console
* SOCKS5 proxy mode allows mitmproxy to act as a SOCKS5 proxy server
* Data streaming for response bodies exceeding a threshold
  (bradpeabody@gmail.com)
* Ignore hosts or IP addresses, forwarding both HTTP and HTTPS traffic
  untouched
* Finer-grained control of traffic replay, including options to ignore
  contents or parameters when matching flows (marcelo.glezer@gmail.com)
* Pass arguments to inline scripts
* Configurable size limit on HTTP request and response bodies
* Per-domain specification of interception certificates and keys (see
  --cert option)
* Certificate forwarding, relaying upstream SSL certificates verbatim (see
  --cert-forward)
* Search and highlighting for HTTP request and response bodies in
  mitmproxy console (pedro@worcel.com)
* Transparent proxy support on Windows
* Improved error messages and logging
* Support for FreeBSD in transparent mode, using pf (zbrdge@gmail.com)
* Content view mode for WBXML (davidshaw835@air-watch.com)
* Better documentation, with a new section on proxy modes
* Generic TCP proxy mode
* Countless bugfixes and other small improvements
* pathod: Hugely improved SSL support, including dynamic generation of certificates
  using the mitproxy cacert

## 7 November 2014: pathod 0.11

* Hugely improved SSL support, including dynamic generation of certificates
  using the mitproxy cacert
* pathoc -S dumps information on the remote SSL certificate chain
* Big improvements to fuzzing, including random spec selection and memoization to avoid repeating randomly generated patterns
* Reflected patterns, allowing you to embed a pathod server response specification in a pathoc request, resolving both on client side. This makes fuzzing proxies and other intermediate systems much better.

## 28 January 2014: mitmproxy 0.10

* Support for multiple scripts and multiple script arguments
* Easy certificate install through the in-proxy web app, which is now
  enabled by default
* Forward proxy mode, that forwards proxy requests to an upstream HTTP server
* Reverse proxy now works with SSL
* Search within a request/response using the "/" and "n" shortcut keys
* A view that beatifies CSS files if cssutils is available
* Bug fix, documentation improvements, and more.

## 25 August 2013: mitmproxy 0.9.2

* Improvements to the mitmproxywrapper.py helper script for OSX.
* Don't take minor version into account when checking for serialized file
  compatibility.
* Fix a bug causing resource exhaustion under some circumstances for SSL
  connections.
* Revamp the way we store interception certificates. We used to store these
  on disk, they're now in-memory. This fixes a race condition related to
  cert handling, and improves compatibility with Windows, where the rules
  governing permitted file names are weird, resulting in errors for some
  valid IDNA-encoded names.
* Display transfer rates for responses in the flow list.
* Many other small bugfixes and improvements.

## 25 August 2013: pathod 0.9.2

* Adapt to interface changes in netlib

## 16 June 2013: mitmproxy 0.9.1

* Use "correct" case for Content-Type headers added by mitmproxy.
* Make UTF environment detection more robust.
* Improved MIME-type detection for viewers.
* Always read files in binary mode (Windows compatibility fix).
* Some developer documentation.

## 15 May 2013: mitmproxy 0.9

* Upstream certs mode is now the default.
* Add a WSGI container that lets you host in-proxy web applications.
* Full transparent proxy support for Linux and OSX.
* Introduce netlib, a common codebase for mitmproxy and pathod
  (http://github.com/cortesi/netlib).
* Full support for SNI.
* Color palettes for mitmproxy, tailored for light and dark terminal
  backgrounds.
* Stream flows to file as responses arrive with the "W" shortcut in
  mitmproxy.
* Extend the filter language, including ~d domain match operator, ~a to
  match asset flows (js, images, css).
* Follow mode in mitmproxy ("F" shortcut) to "tail" flows as they arrive.
* --dummy-certs option to specify and preserve the dummy certificate
  directory.
* Server replay from the current captured buffer.
* Huge improvements in content views. We now have viewers for AMF, HTML,
  JSON, Javascript, images, XML, URL-encoded forms, as well as hexadecimal
  and raw views.
* Add Set Headers, analogous to replacement hooks. Defines headers that are set
  on flows, based on a matching pattern.
* A graphical editor for path components in mitmproxy.
* A small set of standard user-agent strings, which can be used easily in
  the header editor.
* Proxy authentication to limit access to mitmproxy
* pathod: Proxy mode. You can now configure clients to use pathod as an
  HTTP/S proxy.
* pathoc: Proxy support, including using CONNECT to tunnel directly to
  targets.
* pathoc: client certificate support.
* pathod: API improvements, bugfixes.

## 15 May 2013: pathod 0.9 (version synced with mitmproxy)

* Pathod proxy mode. You can now configure clients to use pathod as an
  HTTP/S proxy.
* Pathoc proxy support, including using CONNECT to tunnel directly to
  targets.
* Pathoc client certificate support.
* API improvements, bugfixes.

## 16 November 2012: pathod 0.3

A release focusing on shoring up our fuzzing capabilities, especially with
pathoc.

* pathoc -q and -r options, output full request and response text.
* pathod -q and -r options, add full request and response text to pathod's
  log buffer.
* pathoc and pathod -x option, makes -q and -r options log in hex dump
  format.
* pathoc -C option, specify response codes to ignore.
* pathoc -T option, instructs pathoc to ignore timeouts.
* pathoc -o option, a one-shot mode that exits after the first non-ignored
  response.
* pathoc and pathod -e option, which explains the resulting message by
  expanding random and generated portions, and logging a reproducible
  specification.
* Streamline the specification language. HTTP response message is now
  specified using the "r" mnemonic.
* Add a "u" mnemonic for specifying User-Agent strings. Add a set of
  standard user-agent strings accessible through shortcuts.
* Major internal refactoring and cleanup.
* Many bugfixes.

## 22 August 2012: pathod 0.2

* Add pathoc, a pathological HTTP client.
* Add libpathod.test, a truss for using pathod in unit tests.
* Add an injection operator to the specification language.
* Allow Python escape sequences in value literals.
* Allow execution of requests and responses from file, using the new + operator.
* Add daemonization to Pathod, and make it more robust for public-facing use.
* Let pathod pick an arbitrary open port if -p 0 is specified.
* Move from Tornado to netlib, the network library written for mitmproxy.
* Move the web application to Flask.
* Massively expand the documentation.

## 5 April 2012: mitmproxy 0.8

* Detailed tutorial for Android interception. Some features that land in
  this release have finally made reliable Android interception possible.
* Upstream-cert mode, which uses information from the upstream server to
  generate interception certificates.
* Replacement patterns that let you easily do global replacements in flows
  matching filter patterns. Can be specified on the command-line, or edited
  interactively.
* Much more sophisticated and usable pretty printing of request bodies.
  Support for auto-indentation of Javascript, inspection of image EXIF
  data, and more.
* Details view for flows, showing connection and SSL cert information (X
  keyboard shortcut).
* Server certificates are now stored and serialized in saved traffic for
  later analysis. This means that the 0.8 serialization format is NOT
  compatible with 0.7.
* Many other improvements, including bugfixes, and expanded scripting API,
  and more sophisticated certificate handling.

## 20 February 2012: mitmproxy 0.7

* New built-in key/value editor. This lets you interactively edit URL query
  strings, headers and URL-encoded form data.
* Extend script API to allow duplication and replay of flows.
* API for easy manipulation of URL-encoded forms and query strings.
* Add "D" shortcut in mitmproxy to duplicate a flow.
* Reverse proxy mode. In this mode mitmproxy acts as an HTTP server,
  forwarding all traffic to a specified upstream server.
* UI improvements - use unicode characters to make GUI more compact,
  improve spacing and layout throughout.
* Add support for filtering by HTTP method.
* Add the ability to specify an HTTP body size limit.
* Move to typed netstrings for serialization format - this makes 0.7
  backwards-incompatible with serialized data from 0.6!

* Significant improvements in speed and responsiveness of UI.
* Many minor bugfixes and improvements.

## 7 August 2011: mitmproxy 0.6

* New scripting API that allows much more flexible and fine-grained
  rewriting of traffic. See the docs for more info.
* Support for gzip and deflate content encodings. A new "z"
  keybinding in mitmproxy to let us quickly encode and decode content, plus
  automatic decoding for the "pretty" view mode.
* An event log, viewable with the "v" shortcut in mitmproxy, and the
  "-e" command-line flag in mitmdump.
* Huge performance improvements: mitmproxy interface, loading
  large numbers of flows from file.
* A new "replace" convenience method for all flow objects, that does a
  universal regex-based string replacement.
* Header management has been rewritten to maintain both case and order.
* Improved stability for SSL interception.
* Default expiry time on generated SSL certs has been dropped to avoid an
  OpenSSL overflow bug that caused certificates to expire in the distant
  past on some systems.
* A "pretty" view mode for JSON and form submission data.
* Expanded documentation and examples.
* Countless other small improvements and bugfixes.

## 27 June 2011: mitmproxy 0.5

* An -n option to start the tools without binding to a proxy port.
* Allow scripts, hooks, sticky cookies etc. to run on flows loaded from
  save files.
* Regularize command-line options for mitmproxy and mitmdump.
* Add an "SSL exception" to mitmproxy's license to remove possible
  distribution issues.
* Add a --cert-wait-time option to make mitmproxy pause after a new SSL
  certificate is generated. This can pave over small discrepancies in
  system time between the client and server.
* Handle viewing big request and response bodies more elegantly. Only
  render the first 100k of large documents, and try to avoid running the
  XML indenter on non-XML data.
* BUGFIX: Make the "revert" keyboard shortcut in mitmproxy work after a
  flow has been replayed.
* BUGFIX: Repair a problem that sometimes caused SSL connections to consume
  100% of CPU.

## 30 March 2011: mitmproxy 0.4

* Full serialization of HTTP conversations
* Client and server replay
* On-the-fly generation of dummy SSL certificates
* mitmdump has "grown up" into a powerful tcpdump-like tool for HTTP/S
* Dozens of improvements to the mitmproxy console interface
* Python scripting hooks for programmatic modification of traffic

## 01 March 2010: mitmproxy 0.2

* Big speed and responsiveness improvements, thanks to Thomas Roth
* Support urwid 0.9.9
* Terminal beeping based on filter expressions
* Filter expressions for terminal beeps, limits, interceptions and sticky
  cookies can now be passed on the command line.
* Save requests and responses to file
* Split off non-interactive dump functionality into a new tool called
  mitmdump
* "A" will now accept all intercepted connections
* Lots of bugfixes
