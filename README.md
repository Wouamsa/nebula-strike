# 🚀 Nebula Strike

A free, standalone browser-based asteroid shooter game — no server, no install, no dependencies.

![Game Preview](preview.png)

## 🎮 Play

Just open `nebula_strike.html` in any modern browser. That's it.

▶ [**Live Demo**](https://wouam.fr/nebula_strike.html) *(if you have a hosted version)*

---

## 🕹️ How to Play

| Control | Action |
|--------|--------|
| `←` `→` | Rotate ship |
| `↑` | Thrust |
| `Space` | Shoot |
| `S` | Shield (limited) |

- Destroy asteroids to score points
- Large asteroids split into smaller ones
- Survive as many waves as possible
- Score **5000+** to enter the Hall of Fame

### Scoring

| Target | Points |
|--------|--------|
| Large asteroid | 20 pts |
| Medium asteroid | 50 pts |
| Small asteroid | 100 pts |

Speed multiplier increases with each wave.

---

## ✨ Features

- Pure HTML5 Canvas — no framework, no dependencies
- Procedural asteroid generation
- Particle explosion effects
- Shield mechanic with cooldown
- Hall of Fame (top 5, stored in `localStorage`)
- Pseudo / nickname entry for high scores
- Scrolling HOF ticker
- Mobile-friendly (touch controls via on-screen pad)
- Keyboard: arrows + space + S | ZQSD layout supported

---

## 🗂️ Files

```
nebula_strike.html   ← single file, everything included
README.md
```

All scores are saved locally in the browser (`localStorage`). No backend required.

---

## 🔧 Integrate with a PHP backend (optional)

If you want persistent leaderboards across players, you can plug in a backend:

1. Create a `asteroids_tracker.php` endpoint that handles:
   - `POST {score, wave, pseudo}` → insert score
   - `GET ?action=hof` → return top 10 as JSON `[{pseudo, score, wave, played_at}]`

2. In `nebula_strike.html`, replace the `saveScore()` and `loadHOF()` functions with `fetch()` calls to your endpoint.

Example SQL table:
```sql
CREATE TABLE asteroids_scores (
  id         INT AUTO_INCREMENT PRIMARY KEY,
  score      INT          NOT NULL DEFAULT 0,
  wave       INT          NOT NULL DEFAULT 1,
  pseudo     VARCHAR(12)  DEFAULT NULL,
  ip_address VARCHAR(45),
  played_at  DATETIME     DEFAULT NOW()
);
```

---

## 📄 License

MIT — free to use, modify and redistribute.
