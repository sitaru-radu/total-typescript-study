# Cum învățăm TypeScript aici

Background: Java + C#, **zero TypeScript**. Cartea e sursa principală. Eu sunt partenerul de digestie, nu un shortcut către soluții.

## Ordinea resurselor (nu le amesteca)

1. **Cartea** — citești un slice, nu un capitol întreg din prima.
2. **Exercițiul** din `src/` — `pnpm exercise`, fără `*.solution`.
3. **Handbook** — doar pagina relevantă când te blochezi: [typescriptlang.org/docs/handbook](https://www.typescriptlang.org/docs/handbook/intro.html).
4. **Articole Total TypeScript** — după capitol, ca deepening, nu înainte.
5. **Tutoriale** (Beginner / React / Zod / Errors) — opționale, după ce fundamentele stau.

Cartea e traseul. Restul e hartă și referință.

## Loop-ul (fiecare slice)

1. Citești 5–15 minute din carte (sau explainer-ul din repo).
2. Rulezi problema. Citești eroarea. Încerci.
3. Dacă te blochezi 10 minute: întreabă-mă. Îți explic modelul, nu lipesc soluția.
4. Compari cu `*.solution` **după** ce ai o încercare.
5. Scrii 3 bullet-uri în `study/notes/` cu **cuvintele tale**.
6. Bifezi în `study/PROGRESS.md`.

Un capitol e „gata” doar când poți spune ideea principală fără să te uiți.

## Reguli ca să rămână eficient

- Nu sărim la generice până nu stau **union + narrowing** (capitolele 4–5).
- Nu încadrăm totul în `class` din reflex C#/Java. În TS, funcțiile libere + obiecte sunt default-ul.
- Analogia Java/C# e permisă **și apoi o spargem**. Unde analogia minte e exact locul de învățat.
- JavaScript-ul runtime se învață *pe măsură ce apare*, nu ca un curs separat înainte. TS nu schimbă ce rulează.
- Copilot/autocomplete de soluții: oprit pe `*.problem.*` dacă te ispitește. Editorul ca profesor (hover, eroare) e un feature al cărții.

## Prima sesiune (asta urmează)

1. Citește harta: [MENTAL-MAP.md](MENTAL-MAP.md) + pagina [TypeScript for Java/C# Programmers](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-oop.html).
2. Capitolele 1–3 (setup, IDE, pipeline) — scurte, practice. Le facem ca să ai `tsc` și editorul în mână.
3. Capitolul 4 e unde începe limbajul. Nu grăbi 1–3, dar nu le trata ca pe teorie grea.

Când zici „hai”, începem cu capitolul 1 + primul explainer din `src/005-kickstart-your-typescript-setup`.
