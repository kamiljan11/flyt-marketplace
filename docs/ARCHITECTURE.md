# ARCHITECTURE — mapa dla obcego (1 strona)

**To repo nie zawiera kodu aplikacji.** Jest to publiczny write-up opisujący Flyt — marketplace
frachtowy do i z Islandii (licytacja przewoźników, wspólne kampanie kontenerowe, wyceny importu
na żądanie).

## Co to jest (3 zdania)
Krótki, nietechniczny opis produktu Flyt: dla kogo jest, jaki problem rozwiązuje (transport do/z
Islandii bez własnej floty), jak wygląda model (przewoźnicy licytują zlecenia, klienci dzielą
koszt kontenera w kampaniach grupowych). Nie ma tu ani jednej linii kodu aplikacji.

## Gdzie jest prawdziwy kod
Żywy produkt działa pod [flyt.is](https://flyt.is). Jego źródło leży w **prywatnym** repozytorium
`is-move-magic` — NIE jest publicznie dostępne, więc ten dokument nie może linkować do jego
`docs/ARCHITECTURE.md` tak jak siostrzany write-up `ekomoc-crm` linkuje do publicznego `ekomoc`.
Stack własnego (prywatnego) źródła wg README: React/TypeScript/Supabase/Vercel/n8n.

## Zawartość tego repo
| Plik | Rola |
|---|---|
| `README.md` | opis nietechniczny + wskazanie, że kod jest prywatny |
| `CHANGELOG.md` | historia zmian TEGO repo (write-up), nie aplikacji |
| `docs/RUNBOOK.md`, `docs/REVIEW-LEARNINGS.md`, `docs/adr/` | szablony PG — puste, bo brak kodu do prowadzenia w tym repo |
| `e2e/smoke.spec.ts` | placeholder Playwright — NIE URUCHAMIA SIĘ (brak `package.json`, `playwright.config.ts`, serwera do przetestowania) |
| `LICENSE` | All rights reserved — Mountain All Service ehf. (MAS Group) / Kamil Jan |

## Dlaczego brak CI
Brak `package.json` = brak czego budować/lintować/testować. Workflow, którego wszystkie kroki
same się pomijają (`hashFiles('package.json') != ''`), byłby czystym teatrem. Realne bramki
jakości (build/lint/typecheck/test/audit/gitleaks/semgrep) żyją w prywatnym repo `is-move-magic`,
gdzie faktycznie jest co sprawdzać.

## Jak to cofnąć / kill switch
Nie dotyczy — repo to statyczny opis, nie działający system. Żywy produkt (flyt.is) ma własny
kill switch w swoim (prywatnym) repo.
