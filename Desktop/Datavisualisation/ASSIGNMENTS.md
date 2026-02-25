# Completed Assignments

A summary of all assignments completed in this repository session.

---

## 1. The Basics of GitHub

**Repo:** [git-fundamentals](https://github.com/pascal-maker/git-fundamentals)

### What was covered
- Git as a distributed Version Control System
- GitHub flow: repositories, cloning, committing, pushing
- Branches, forks, pull requests, issues
- Markdown on GitHub
- GitHub community features (stars, following, Explore)

### What was delivered
| File | Description |
|------|-------------|
| `README.md` | Original course content |
| `my-learning.md` | Personal reflection: what was learned and what to explore next |

### Git workflow used
- Created `feature/github-learning-notes` branch
- Committed `my-learning.md`
- Opened PR → merged into `main`

---

## 2. Merge Conflict Demo — Basic

**Repo:** [merge-demo](https://github.com/pascal-maker/merge-demo)

### What was covered
- How merge conflicts are created (two branches modifying the same line)
- Reading Git conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
- Resolving a conflict and committing the resolution

### Scenario
- `main` branch: changed `h1` color to **green**
- `feature-branch`: changed `h1` color to **red**
- Merging caused a conflict in `style.css` → resolved by keeping green

### Files
| File | Description |
|------|-------------|
| `index.html` | Simple webpage with an `h1` heading |
| `style.css` | Stylesheet where the conflict occurred |
| `README.md` | Documents the conflict, markers, and resolution |

### Branches
| Branch | Role |
|--------|------|
| `main` | Resolved — green color |
| `feature-branch` | Red color |

---

## 3. Merge Conflict Demo — Advanced E-commerce

**Repo:** [merge-demo-project](https://github.com/pascal-maker/merge-demo-project)

### What was covered
- Multi-file merge conflicts across `Product.js` and `pricing.js`
- Resolving conflicts that require combining logic from both branches
- Business logic awareness: discount applied **before** tax

### Scenario
Two teams worked in parallel:
- **Team A (`feature-discount`):** implemented `getDiscount()` and updated `calculatePrice()`
- **Team B (`feature-tax`):** implemented `getTax()` and updated `calculatePrice()`

Merging `feature-tax` into `main` (after `feature-discount` was already merged) caused conflicts in both files.

### Resolution
```js
// Product.js — combined both features
calculatePrice() {
  const priceWithDiscount = this.basePrice - this.getDiscount();
  return priceWithDiscount + this.getTax(priceWithDiscount);
}
```

### Files
| File | Description |
|------|-------------|
| `src/components/Product.js` | Product class — conflicted and resolved |
| `src/components/Cart.js` | Cart class |
| `src/utils/pricing.js` | calculateTotal — conflicted and resolved |
| `README.md` | Documents the scenario, conflicts, and resolution |

### Branches
| Branch | Role |
|--------|------|
| `main` | Resolved — discount + tax combined |
| `feature-discount` | Discount system only |
| `feature-tax` | Tax system only |

---

## 4. Chess — OOP & Git Assignment

**Repo:** [chess](https://github.com/pascal-maker/chess)

### What was covered
- Object-Oriented Programming with Python
- Inheritance using `ABC` (Abstract Base Class)
- `dict` inheritance for JSON serialisation
- Python decorators (`@print_board`, `@save_board`)
- Dict and list comprehensions
- Generators (`load_board_states`)
- Static methods (`BoardMovements`)
- Git feature branch workflow

### Files
| File | Description |
|------|-------------|
| `pieces.py` | `BaseChessPiece(ABC, dict)` + 6 piece classes with movement logic and decorators |
| `board.py` | `Board` class: dict comprehension setup, `print_board`, `find_piece`, `save_board_state`, `load_board_states` generator |
| `board_movements.py` | `BoardMovements` static class: 8 directional movement helpers, color-aware forward/backward |
| `main.py` | Demo: board setup, moves, board auto-printing, state replay |
| `board.txt` | Saved board states (JSON, one per line) |
| `README.md` | Documents structure, concepts, branches, and movement table |

### Key concepts implemented
| Concept | Where |
|---------|-------|
| Inheritance | `BaseChessPiece` → `Pawn`, `Rook`, `Bishop`, `Knight`, `Queen`, `King` |
| Decorators | `@print_board`, `@save_board` on `BaseChessPiece.move()` |
| Dict comprehension | Board squares init + pawn placement in `Board.setup_board()` |
| List comprehension | `print_board()` row builder, `find_piece()` filter |
| Generator | `Board.load_board_states()` — reads `board.txt` one line at a time |
| Static methods | All 8 direction helpers in `BoardMovements` |
| `dict` inheritance | `BaseChessPiece(ABC, dict)` — enables `json.dumps` serialisation |

### Branches
| Branch | Role |
|--------|------|
| `main` | Fully merged implementation |
| `feature/chess-pieces` | All 6 piece classes |
| `feature/board-setup` | `Board` + `BoardMovements` |
| `feature/decorators-and-state` | Decorators + save/load state |

---

## Summary Table

| # | Assignment | Repo | Key concepts |
|---|-----------|------|-------------|
| 1 | GitHub Basics | [git-fundamentals](https://github.com/pascal-maker/git-fundamentals) | Git flow, branches, PRs, issues |
| 2 | Merge Conflict — Basic | [merge-demo](https://github.com/pascal-maker/merge-demo) | Conflict markers, single-file resolution |
| 3 | Merge Conflict — Advanced | [merge-demo-project](https://github.com/pascal-maker/merge-demo-project) | Multi-file conflicts, business logic |
| 4 | Chess OOP | [chess](https://github.com/pascal-maker/chess) | Inheritance, decorators, generators, comprehensions |
