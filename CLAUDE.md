# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

`pharn-web` is a static deployment whose entire purpose is to redirect all traffic to the `pharn-dev/pharn-oss` GitHub repository. It has no application code, build step, or test suite — it is configuration only.

## Architecture

The whole behavior lives in `vercel.json`. Two redirects are defined:

- `/` → `https://github.com/pharn-dev/pharn-oss` (permanent / 308)
- `/(.*)` → same destination (permanent / 308) — catches every other path

Both are `permanent: true`, so Vercel issues 308 redirects that browsers and search engines cache. Changing the destination means clients may keep the old target cached; bump intentionally.

## Deployment

Deployed via Vercel. There is no local dev server or build — Vercel reads `vercel.json` directly. Pushing to `main` (remote: `github.com:pharn-dev/pharn-web.git`) triggers a Vercel deploy.
