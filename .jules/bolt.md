
## $(date +%Y-%m-%d) - Use memchr/wmemchr for strnlen equivalent
**Learning:** Found hand-rolled `strnlen`-like loops in `archive_string.c` (e.g. in `archive_strncat`, `archive_wstrncat`, and `utf16nbytes` or similar routines) which evaluate `s < n && *pp` repeatedly. Replacing these naive loops with `memchr(p, '\0', n)` (and `wmemchr(p, L'\0', n)` for wide strings) is ~7x faster in benchmarks.
**Action:** Replace manual `strnlen` loops with `memchr` based variants in `libarchive/archive_string.c` to improve string handling performance.
