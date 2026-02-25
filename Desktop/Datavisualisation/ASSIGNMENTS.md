# My Learning Journey — Git, GitHub & Python OOP

*by Pascal Musabyimana*

---

When I started these assignments I already had some experience with Git — pushing code, pulling updates, the usual routine. But I quickly realised there was a gap between knowing the commands and actually understanding what Git is doing underneath. These four assignments closed that gap in a way that stuck.

---

## Starting with the Basics — GitHub Fundamentals

**Repo:** [git-fundamentals](https://github.com/pascal-maker/git-fundamentals)

The GitHub Basics course was not difficult, but it was grounding. It forced me to slow down and think about things I had been taking for granted. Git is a *distributed* version control system — meaning every developer has a full copy of the entire history, not just the latest snapshot. That sounds obvious until you really sit with it and realise why it matters: you can work completely offline, roll back to any point in history, and collaborate without a central bottleneck.

What stood out most was the concept of the **GitHub flow** — the rhythm of branching, committing, opening a pull request, getting feedback, and merging. I had done most of these steps before, but always reactively, without thinking of them as a deliberate workflow. After this course I started thinking of a branch not just as a copy of the code, but as a *conversation* with the team about a specific piece of work.

I completed the assignment by writing `my-learning.md` — a personal reflection on what I had learned — on a dedicated feature branch, then opening a pull request and merging it. Even that small exercise made the theory feel real.

---

## When Two Branches Disagree — The Basic Merge Conflict

**Repo:** [merge-demo](https://github.com/pascal-maker/merge-demo)

Merge conflicts used to intimidate me. Seeing those `<<<<<<<` markers in a file felt like Git telling me I had broken something. This assignment changed that completely.

The scenario was simple on purpose: one developer changed an `h1` color to green on `main`, while another changed it to red on `feature-branch`. When we tried to merge, Git couldn't decide which color was "right" — so it stopped and asked us to decide. That is not a failure. That is Git doing exactly what it should.

```
h1 {
    color: green;
    font-size: 24px;
}
```

Once I understood that those markers are just Git's way of saying *"both of these changes are valid, I just need a human to make the call"*, the anxiety disappeared. A merge conflict is not a bug in your workflow. It is proof that your version control system is protecting you from silently overwriting someone else's work.

I resolved it, committed the fix, and pushed. Clean. What had felt scary before now felt like a normal part of development.

---

## When It Gets Real — Multi-File Conflicts in an E-commerce Project

**Repo:** [merge-demo-project](https://github.com/pascal-maker/merge-demo-project)

The advanced challenge was where things got genuinely interesting. Instead of one file and one conflict, I was now dealing with two teams who had been working in parallel on an e-commerce application — both touching the same files, both with completely valid work, both needing to coexist.

Team A had built a discount system. Team B had built a tax calculator. On their own, each implementation made perfect sense. Together, they conflicted — not just technically, but *logically*. Merging them was not just a matter of picking one version over the other. I had to think about the business: should the discount be applied before or after tax? In standard retail, yes — you discount first, then apply tax to the reduced price. The code had to reflect that.

```js
calculatePrice() {
  const priceWithDiscount = this.basePrice - this.getDiscount();
  return priceWithDiscount + this.getTax(priceWithDiscount);
}
```

This was the lesson I did not expect: resolving a merge conflict is sometimes a *product decision*, not just a technical one. Understanding the code is not enough — you need to understand the domain it operates in. That insight changed how I think about code review and collaboration entirely.

---

## Building Something — Chess in Python

**Repo:** [chess](https://github.com/pascal-maker/chess)

The chess assignment was the most ambitious of the four and the one I am most proud of. It brought together everything: OOP, inheritance, decorators, comprehensions, generators, static methods, and a proper Git branching workflow — all in one project.

I started with a `BaseChessPiece` class that inherited from both `ABC` and Python's built-in `dict`. The `dict` inheritance was an elegant trick — it meant every piece was automatically JSON-serialisable, so saving the board state to a file became a single line. The abstract base class established the contract: every piece *must* know how to move, even if the mechanics differ wildly between a Pawn and a Knight.

What I found most satisfying was the decorator work. The `@print_board` and `@save_board` decorators on the `move()` method meant that every time any piece moved, the board was automatically printed and the state saved — without any piece needing to know about that. The separation of concerns felt clean. A Pawn just calculates where it should go. The decorator handles the side effects.

```python
@print_board
@save_board
def move(self, movement: str):
    # move the piece on the board
```

The generator for loading saved board states was another highlight. Instead of reading the entire `board.txt` file into memory at once, the generator yields one line at a time — the kind of detail that does not matter for 3 moves but matters enormously when you have been playing for hours and the file has thousands of states.

I also had to think carefully about direction. BLACK starts at rows 1–2, WHITE at rows 7–8. So "forward" means something different depending on which color you are playing. That one detail — making movement color-aware — was a small thing that made the whole simulation feel honest.

By the end, the board printed exactly as expected:

```
[BLACK Rook 1, BLACK Knight 1, BLACK Bishop 1, BLACK Queen 1, BLACK King 1, BLACK Bishop 2, BLACK Knight 2, BLACK Rook 2]
[BLACK Pawn 1, BLACK Pawn 2, BLACK Pawn 3, BLACK Pawn 4, BLACK Pawn 5, BLACK Pawn 6, BLACK Pawn 7, BLACK Pawn 8]
[None, None, None, None, None, None, None, None]
...
[WHITE Pawn 1, WHITE Pawn 2, WHITE Pawn 3, WHITE Pawn 4, WHITE Pawn 5, WHITE Pawn 6, WHITE Pawn 7, WHITE Pawn 8]
[WHITE Rook 1, WHITE Knight 1, WHITE Bishop 1, WHITE Queen 1, WHITE King 1, WHITE Bishop 2, WHITE Knight 2, WHITE Rook 2]
```

Running `python main.py` and seeing that output for the first time was genuinely satisfying.

---

## Looking Back

These four assignments tell a connected story. I started by understanding the *philosophy* of Git, moved into the *mechanics* of conflict resolution, discovered that good conflict resolution requires *domain knowledge*, and finally built a full OOP application using Git branching as the backbone of the development process.

The thing that surprised me most is how much of software development is about communication — with your team through branches and pull requests, with future readers through commit messages and READMEs, and even with yourself through clean, well-structured code. Git is not just a backup tool. It is a collaboration protocol.

I am looking forward to going deeper — particularly into `git rebase`, GitHub Actions for automated testing, and protected branch rules for team projects. But the foundation is solid now.

---

| Assignment | Repo | Core lesson |
|-----------|------|------------|
| GitHub Basics | [git-fundamentals](https://github.com/pascal-maker/git-fundamentals) | Git is a collaboration protocol, not just a backup tool |
| Merge Conflict — Basic | [merge-demo](https://github.com/pascal-maker/merge-demo) | Conflicts are Git protecting you, not punishing you |
| Merge Conflict — Advanced | [merge-demo-project](https://github.com/pascal-maker/merge-demo-project) | Resolving conflicts requires understanding the domain |
| Chess OOP | [chess](https://github.com/pascal-maker/chess) | Clean abstractions make complex systems manageable |
