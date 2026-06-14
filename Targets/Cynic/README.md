# Target: Cynic

[Cynic](https://github.com/chicoxyzzy/cynic) is a strict-only ECMAScript
engine written in Zig. Unlike the other targets it needs no patches: REPRL
support, the `fuzzilli()` builtin, and `-fsanitize-coverage=trace-pc-guard`
instrumentation are built into the engine.

To build Cynic for fuzzing:

1. Clone Cynic from https://github.com/chicoxyzzy/cynic
2. Run `zig build fuzz` in the cynic directory
3. zig-out/bin/cynic-fuzz will be the JavaScript shell for the fuzzer

Cynic is strict-only and implements no Annex B; the `cynic` profile runs it
with the SES posture and the eval gate relaxed (both baked into the
cynic-fuzz binary), the same posture Cynic scores test262 under.
