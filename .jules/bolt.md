## 2026-10-22 - Optimize `archive_strncat` performance using `memchr`
**Learning:** We can optimize the C loop in `archive_strncat` using `memchr` rather than a `while` loop which checks each character. `memchr` is heavily optimized in libc and vectorised.
**Action:** Replace `while (s < n && *pp)` with `memchr(p, '\0', n)` when calculating `strnlen`-like limits on buffers.
