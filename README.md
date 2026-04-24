# Muffin AI — Meeting Log

Pagina statica per allineare il management sui meeting svolti col team AI. Un file unico, niente build.

## Deploy su GitHub Pages

1. Crea una repo GitHub
2. `git init && git add . && git commit -m "init" && git push`
3. Su GitHub: **Settings → Pages → Source: main / root**
4. Online su `https://<user>.github.io/<repo>` entro ~1 minuto

## Aggiornare dopo un meeting

Apri `index.html` e scorri fino a `const SESSIONS = [...]`. Aggiungi una nuova entry in cima (o compila il placeholder esistente):

```js
{
  date: "2026-05-08",
  title: "Sprint Review · D3",
  subtitle: "Core RAG + frontend integration",
  summary: "Frase di sintesi per il management.",
  quadro: [
    "Punto emerso 1 (può usare <b>grassetto</b>, <i>corsivo</i>, <code>code</code>).",
    "Punto emerso 2.",
  ],
  decisioni: [
    "<b>Decisione X</b>: dettaglio.",
    "<b>Decisione Y</b>: dettaglio.",
  ],
}
```

Aggiorna `LAST_UPDATE` in alto, poi `git commit -am "meeting 08/05" && git push`.

### Campi disponibili

- `date` — `YYYY-MM-DD` (obbligatorio)
- `title` — titolo breve (obbligatorio)
- `subtitle` — sottotitolo opzionale
- `recording` — URL della registrazione (es. Read.ai)
- `summary` — paragrafo di sintesi nel box arancione
- `quadro` — array di stringhe HTML: cosa è emerso dalla discussione
- `decisioni` — array di stringhe HTML: cosa è stato deciso
- `latest: true` — pallino arancione pieno (ultima sessione)
- `placeholder: "testo"` — mostra un box "in attesa", per meeting in corso

Le sessioni si ordinano secondo l'ordine nell'array (la prima è espansa di default).
