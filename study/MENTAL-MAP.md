# Harta mentală: Java/C# → TypeScript

Păstrează 4 idei. Restul e detalii care se agață de ele.

## 1. TypeScript nu e un runtime nou

C# și Java **compilează la un bytecode care încă cunoaște tipurile**. TypeScript compilează (sau e verificat) către **JavaScript**. Tipurile dispar. `typeof` / `instanceof` văd valori JS, nu `T` din generice.

Consecință: validarea la granițe (JSON, `process.env`, input HTTP) e treabă de **runtime** (mai târziu: Zod). Tipurile nu te apără după ce programul a pornit.

## 2. Un tip e o mulțime de valori

În C#/Java, o valoare are *un* tip nominal (clasa ei). În TS, o valoare poate aparține **mai multor mulțimi** deodată.

- `string | number` e reuniunea a două mulțimi — natural, nu un hack.
- Narrowing ( `if`, `typeof`, discriminated unions) **taie** mulțimea până rămâne ce e sigur.
- `never` e mulțimea vidă. `unknown` e „tot ce există, dar nu știu încă”.

Când un geneneric sau un union te încurcă, întreabă: *ce valori sunt încă posibile aici?*

## 3. Tipurile sunt structurale, nu nominale

Dacă arată ca `Point` (`x: number`, `y: number`), *este* un `Point` pentru checker — chiar dacă n-ai scris `implements Point`.

Capcane clasice din OOP:

- Două clase cu aceleași metode sunt asignabile una alteia.
- Tipul gol `{}` / o clasă fără câmpuri acceptă aproape orice obiect.
- Nu ai nevoie de o ierarhie ca să partajezi o formă. O `interface` descrie *shape*, nu o identitate de clasă.

## 4. Clasa nu e unitatea de program

În JS/TS, datele și funcțiile trăiesc și **în afara** claselor. Singleton / static class din C# sunt de obicei un modul + funcții.

Folosește clase când ai identitate, instanță, `this` — nu ca pe folderul default.

---

## Tabel de traducere (și unde minte)

| Obicei Java/C# | În TypeScript | Capcana |
| --- | --- | --- |
| Totul e o clasă | Funcții + obiecte + module | Over-engineering cu `class` |
| Tipuri nominale | Tipuri structurale | `Car` și `Golfer` cu `drive()` sunt compatibile |
| Tipuri reificate (`typeof(T)`) | Tipuri șterse | Genericele nu există la runtime |
| `null` | `null` **și** `undefined` | Două „lipsuri”, nu una |
| `List<T>` / `IEnumerable<T>` | `T[]`, uneori `Array<T>` | Aceleași; `T[]` e stilul uzual |
| Overload real | Overload doar în tipuri | La runtime e o singură funcție |
| `interface` = contract pe clasă | `interface` / `type` = shape | Nu trebuie `implements` ca să treacă |
| `private` e enforcement | `private` e (aproape) doar compile-time | Nu e secret față de JS |
| `const` / `readonly` pe referință | `const` nu îngheață obiectul | Mutabilitatea e capitol separat |
| Subclass pentru variante | Union discriminator (`type: "ok"`) | Ierarhia e adesea mai slabă decât un union |
| Excepții checked | Nu există | Erorile sunt `unknown` în `catch` |
| `var` vs `val` | `let` vs `const` | `const` ≠ imutabil |
| `object` / `Object` | `object`, `{}`, `Record<string, unknown>` | Semnifică lucruri diferite; le luăm la cap. 4–6 |

## JavaScript-ul de care ai nevoie (pe parcurs, nu înainte)

Nu facem un curs JS. Când apare în carte, oprește-te 2 minute:

- `let` / `const`, obiecte `{ }`, funcții (inclusiv arrow)
- array methods (`map`, `filter`)
- `===`, `undefined` vs `null`
- `import` / `export`
- Promises / `async`–`await` (îți sunt familiare din C#)

Runtime-ul e JavaScript. TypeScript doar *vorbește despre* el.

## Cum se leagă cartea de aceste 4 idei

| Parte | Capitole | Ideea pe care o instalează |
| --- | --- | --- |
| I Setup | 1–3 | Editorul e profesorul; `tsc` nu e „compilerul C#” |
| II Fundamentals | 4–5 | Anotații + **unions / narrowing** (inima sistemului) |
| III Obiecte | 6–9 | Shape, mutabilitate, clase, features care *nu* există în JS |
| IV Compiler | 10–12 | Derivare, aserțiuni, colțuri ciudate — gândești ca type checker-ul |
| V Mediu | 13–14 | Module, `.d.ts`, `tsconfig` |
| VI Design | 15–16 | Cum îți ții tipurile sănătoase într-o aplicație |

Repo-ul are și extras față de cartea print: CJS vs ESM, types you don’t control, style guide, migrare din JS. Le facem **după** capitolul de carte corespunzător, nu în locul lui.

## Tutoriale și articole — când

| Resursă | Când |
| --- | --- |
| [TS for Java/C# Programmers](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-oop.html) | Sesiunea 0 (acum) |
| Handbook: Basics, Everyday Types, Narrowing | Lângă cap. 4–5 |
| [Beginner’s TypeScript](https://www.totaltypescript.com/tutorials/beginners-typescript) | Doar dacă cap. 4 se simte prea dens |
| Articol: *No, TypeScript Types Don’t Exist At Runtime* | După ce ideea 1 a zgâriat |
| Articol: *Type vs Interface* | După cap. 6 |
| Articol: *Building the Mental Model for Generics* | Înainte de genericele serioase (cap. 10+) |
| [Solving TypeScript Errors](https://www.totaltypescript.com/tutorials/solving-typescript-errors) | Când erorile lungi te sperie (cap. 12 e despre asta) |
| React with TypeScript / Zod | După cap. 9, când vrei aplicație, nu în paralel cu fundamentele |
