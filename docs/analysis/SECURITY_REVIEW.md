# Public Portfolio Security Review

## Result

**No real secret literal was detected in the supplied final ZIP text files using targeted pattern scanning.**

The original project includes `.env.example` only, with empty placeholders such as:

- `OPENAI_API_KEY=`
- `DATABASE_URL=`
- `KMA_SERVICE_KEY=`
- `AIRKOREA_SERVICE_KEY=`
- `FACILITY_SERVICE_KEY=`
- `KAKAO_REST_API_KEY=`
- `KAKAO_JAVASCRIPT_KEY=`

`DJANGO_SECRET_KEY=change-me` is a documented placeholder, not an operational key.

## What this portfolio intentionally excludes

- `.env`
- DB connection strings
- API/service keys
- credentials files
- deployment secret values
- user database exports
- session/cookie data
- full Backend/Data pipeline source copies not needed to explain the portfolio owner's work
- large audio and room asset libraries

## `.gitignore` policy

The portfolio `.gitignore` blocks:

- `.env*` except optional `.env.example`
- key/certificate formats
- credential/secret-named files
- Python virtual environments and SQLite DBs
- local output/build/log files

## Screenshot privacy

Selected screenshots are final demo artifacts from the project repository. The portfolio does not include private friend profile dumps or real user credential screens.

## Before every future push

Recommended commands:

```bash
git status
git diff --cached
```

Optional secret scanner:

```bash
# example if gitleaks is installed
gitleaks detect --source . --no-git
```

Never commit a real `.env` even temporarily. Removing it in a later commit does not remove it from Git history.
