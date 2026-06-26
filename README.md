![GitHub top language](https://img.shields.io/github/languages/top/afiqandico13/warmadewa-web-security-review) ![GitHub license](https://img.shields.io/github/license/afiqandico13/warmadewa-web-security-review)

# Universitas Warmadewa — Web Security Review

> ⚠️ **Status: PRIVATE repository** (default for institutional review). See [Responsible Disclosure](#responsible-disclosure) below.
> Static security analysis of `https://www.warmadewa.ac.id/` (Universitas Warmadewa, Bali).  
> **Method**: Static analysis only. NO active testing, NO login attempts, NO payload submission.  
> **Date**: 18 June 2026

## Quick Summary

Warmadewa runs **Laravel** (PHP framework) on LiteSpeed, behind **Cloudflare**. Overall more secure than typical WordPress deployments — Laravel defaults provide proper CSRF, session management, and cookie security.

| Severity | Count | Key Items |
|---|---|---|
| 🟡 Medium | 3 | Missing HSTS, CSP, X-Frame-Options (and other security headers) |
| 🟢 Low | 0 | (no exploitable findings) |
| ⚪ Info | 1 | Custom cookie (`zesXZsnTWkKIShM7GTNeC6as5KHPUkywfN8OQhYe`) — purpose unclear |

**No active exploit path verified.** Defense-in-depth gap, not exploitable.

## Key Positives (Good Security Foundation)

- ✅ Laravel framework (CSRF protection built-in via `XSRF-TOKEN` cookie)
- ✅ Cookie flags proper: `Secure`, `HttpOnly`, `SameSite=Lax`
- ✅ Session timeout: 2 hours (reasonable)
- ✅ Cloudflare WAF in front
- ✅ No version disclosure (server hidden)
- ✅ No user enumeration (not WordPress)
- ✅ No active XSS patterns on homepage

## What's Missing

- ❌ `Strict-Transport-Security` (HSTS)
- ❌ `Content-Security-Policy` (CSP)
- ❌ `X-Frame-Options` (clickjacking)
- ❌ `X-Content-Type-Options` (MIME sniffing)
- ❌ `Referrer-Policy`
- ❌ `Permissions-Policy`

## Risk Level

🟢 **LOW** — No exploitable vulnerability from public surface. Defense-in-depth needs improvement, but no urgent issues.

## What This Review Covers

- Security headers analysis
- Tech stack detection
- Cookie security analysis
- Form analysis (3 search forms, all GET, no auth)
- Endpoint reconnaissance
- General XSS pattern check

## What This Review Does NOT Cover

- Active testing (XSS, SQLi payloads, brute force)
- Authenticated areas
- Server-side configuration
- Database security
- Laravel-specific dependency check

## Method

- Static analysis (curl + browser DevTools)
- 0 login attempts
- 0 payload submissions
- 0 brute force
- 0 authentication bypass attempts
- All findings reproducible without special access

## Responsible Disclosure

**This report should be shared with Warmadewa IT BEFORE making it public.**

If you're a researcher:
1. Contact Warmadewa IT (look for `admin@warmadewa.ac.id`, `humas@warmadewa.ac.id`, or LinkedIn IT staff)
2. Wait for acknowledgment
3. Coordinate public release
4. NO public disclosure before fix

If you're Warmadewa IT:
- This is constructive feedback
- All recommendations are defense-in-depth
- Fix priority: add security headers (1-2 hours work)
- No active exploitation found

## License

MIT — feel free to use as template.

## Author

**Afiq Andico** — Mahasiswa Sistem Informasi, STIKOM Bali

- Email: afiqandico13@gmail.com
- GitHub: [@afiqandico13](https://github.com/afiqandico13)

## Changelog

- **2026-06-18**: Initial review (static analysis)

---

## 🔗 Related Work

Sibling security research repos dari author yang sama:

- **[sion-stikom-security-review](https://github.com/afiqandico13/sion-stikom-security-review)** — Comprehensive pentest 2026 (5 findings + CVSS scoring) untuk `*.stikom-bali.ac.id`
- **[unud-web-security-review](https://github.com/afiqandico13/unud-web-security-review)** — Static review Universitas Udayana website

**Methodology**: Both reviews mengikuti OWASP Testing Guide v4 dengan responsible disclosure principles.

---

## 📊 Author Portfolio

**Afiq Andico Pangimpian** — IT Support @ Cube Cafe Jimbaran · S1 Sistem Informasi ITB STIKOM Bali

- Email: afiqandico13@gmail.com
- GitHub: [@afiqandico13](https://github.com/afiqandico13)
- Security portfolio: [github.com/afiqandico13?tab=repositories&q=security-review](https://github.com/afiqandico13?tab=repositories&q=security-review)
