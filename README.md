# Relationshapez: Combinatoric Tester

**Combinatoric Tester** is a single-file HTML practice tool for exploring combinations, permutations, and problems that use both ideas. It uses a simple mobile-friendly flashcard layout: one question, two large buttons, three checkbox filters, and a hidden solution card.

## Files

- `index.html` — the main interactive browser tool
- `README.md` — repository overview and usage guide
- `LICENSE` — MIT license text

<https://relationshapez.github.io/combinatoric_tester/>

## How to Use the App

1. Open `index.html` in a browser.
2. Use the three checkboxes at the top to choose which classes of problems should appear:
   - **Combinations**
   - **Permutations**
   - **Combinations and Permutations**
3. Read the question.
4. Try to decide whether the problem uses a combination, a permutation, or both.
5. Press **Solution** to reveal the answer, the type of counting used, and the formula.
6. Press **Refresh** for a new question.

At least one checkbox always remains selected, so the app always has a class of problems to draw from.

The app intentionally does not ask the user to type an answer. This keeps the mobile interface simple and makes the tool work well as a flashcard-style classroom activity.

## Main Idea

A useful first question is:

> Does order matter?

If order does **not** matter, the problem usually involves a **combination**.

If order **does** matter, the problem usually involves a **permutation**.

If the problem asks students to choose objects and then arrange them, assign roles, rank them, seat them, or label them, then the problem uses **both** combinations and permutations.

## Core Formulas

### Combinations

A combination counts groups. Order does not matter.

```text
C(n, r) = n! / (r!(n-r)!)
```

Example:

> In how many ways can 3 students be chosen from a class of 10?

Solution:

```text
C(10, 3) = 120
```

This is a combination because the same 3 students form the same group no matter how they are listed.

### Permutations

A permutation counts arrangements. Order matters.

```text
P(n, r) = n! / (n-r)!
```

Example:

> In how many ways can president, vice president, and treasurer be chosen from 10 students?

Solution:

```text
P(10, 3) = 10 · 9 · 8 = 720
```

This is a permutation because the offices are different roles.

### Factorials

A factorial counts the number of ways to arrange all objects in a group.

```text
n! = n · (n-1) · (n-2) · ... · 2 · 1 = P(n,n)
```

Example:

```text
5! = 5 · 4 · 3 · 2 · 1 = 120
```

## Question Types Included

The app includes three major categories of problems.

---

# 1. Combination Problems

Combination problems ask students to choose a group.

The order of the chosen objects does not matter.

## 1.1 Basic Committees

### Template

```text
In how many ways can a committee of r students be chosen from n students?
```

### Method

Use:

```text
C(n, r)
```

### Example

```text
In how many ways can a committee of 4 students be chosen from 12 students?
```

Solution:

```text
C(12, 4) = 495
```

This is a combination because a committee is just a group.

---

## 1.2 Required Member

### Template

```text
In how many ways can a group of r students be chosen from n students if Alex must be included?
```

### Method

Alex is already chosen. Choose the remaining `r - 1` students from the remaining `n - 1` students.

```text
C(n - 1, r - 1)
```

### Example

```text
In how many ways can a group of 5 students be chosen from 12 students if Alex must be included?
```

Solution:

```text
C(11, 4) = 330
```

---

## 1.3 Forbidden Member

### Template

```text
In how many ways can a group of r students be chosen from n students if Jordan cannot be chosen?
```

### Method

Remove Jordan from the pool. Choose all `r` students from the remaining `n - 1` students.

```text
C(n - 1, r)
```

### Example

```text
In how many ways can a group of 4 students be chosen from 12 students if Jordan cannot be chosen?
```

Solution:

```text
C(11, 4) = 330
```

---

## 1.4 At Least One Special Member

### Template

```text
A club has n students, including s seniors. In how many ways can a committee of r be chosen if at least one senior must be chosen?
```

### Method

Use the complement.

```text
all committees - committees with no seniors
```

So:

```text
C(n, r) - C(n - s, r)
```

### Example

```text
A club has 12 students, including 4 seniors. In how many ways can a committee of 3 be chosen if at least one senior must be chosen?
```

Solution:

```text
C(12, 3) - C(8, 3) = 220 - 56 = 164
```

---

## 1.5 Card Sets with Exactly Some Hearts

### Template

```text
Choose c cards at random from a standard deck that contains 52 cards divided into four suits (spades, hearts, diamonds, and clubs) where each suit consists of 13 cards. How many of the possible sets of c cards will have exactly h hearts?
```

In the app, `c` ranges from 5 through 13, and `h` satisfies `1 < h <= c`.

### Method

A standard deck has 13 hearts and 39 cards that are not hearts. To form a set of `c` cards with exactly `h` hearts, choose the hearts first and then choose the remaining cards from the non-hearts.

```text
C(13, h) · C(39, c - h)
```

This is a combination problem because the question asks for sets of cards. The order in which the cards are drawn or listed does not matter.

### Example

```text
Choose 6 cards at random from a standard deck that contains 52 cards divided into four suits (spades, hearts, diamonds, and clubs) where each suit consists of 13 cards. How many of the possible sets of 6 cards will have exactly 2 hearts?
```

Solution:

```text
C(13, 2) · C(39, 4) = 78 · 82251 = 6415578
```

This uses multiple combinations because the set is built from two categories: hearts and non-hearts.

---

## 1.6 Triangles from Points

### Template

```text
If no three points are collinear, how many triangles can be formed from n points?
```

### Method

A triangle is determined by choosing 3 points.

```text
C(n, 3)
```

### Example

```text
If no three points are collinear, how many triangles can be formed from 10 points?
```

Solution:

```text
C(10, 3) = 120
```

---

## 1.7 Handshakes

### Template

```text
If n people each shake hands with every other person once, how many handshakes occur?
```

### Method

A handshake is determined by choosing a pair of people.

```text
C(n, 2)
```

### Example

```text
If 12 people each shake hands with every other person once, how many handshakes occur?
```

Solution:

```text
C(12, 2) = 66
```

This connects naturally to complete graphs, where every pair of vertices determines an edge.

---

# 2. Permutation Problems

Permutation problems ask students to arrange objects, assign roles, or count ordered outcomes.

The order matters.

## 2.1 Line Arrangements

### Template

```text
In how many ways can n students line up for a photo?
```

### Method

Arrange all `n` students.

```text
n!
```

### Example

```text
In how many ways can 6 students line up for a photo?
```

Solution:

```text
6! = 720
```

---

## 2.2 Circular Arrangements

### Template

```text
In how many ways can n dancers form a circle for a folk dance?
```

### Method

Rotations of the same circle count as the same arrangement. Fix one dancer and arrange the remaining `n - 1` dancers.

```text
(n - 1)!
```

### Example

```text
In how many ways can 7 dancers form a circle for a folk dance?
```

Solution:

```text
6! = 720
```

---

## 2.3 Letter Arrangements with No Repeated Letters

### Template

```text
How many permutations are there of the letters in WORD?
```

### Method

If all letters are distinct, arrange all letters.

```text
n!
```

### Example

```text
How many permutations are there of the letters in GRAPH?
```

Solution:

```text
5! = 120
```

---

## 2.4 Letter Arrangements with Repeated Letters

### Template

```text
How many distinguishable permutations are there of the letters in WORD?
```

### Method

Arrange all letters, then divide by the factorials of repeated letter counts.

```text
n! / (a! b! c! ...)
```

### Examples

```text
MOON: 4! / 2! = 12
LEVEL: 5! / (2!2!) = 30
BANANA: 6! / (3!2!) = 60
LETTER: 6! / (2!2!) = 180
TATTOO: 6! / (2!2!) = 180
```

---

## 2.5 Offices or Roles

### Template

```text
In how many ways can r different offices be filled from n students?
```

### Method

Because the roles are different, order matters.

```text
P(n, r)
```

### Example

```text
In how many ways can 3 different offices be filled from 10 students?
```

Solution:

```text
P(10, 3) = 10 · 9 · 8 = 720
```

---

## 2.6 People Forced Together

### Template

```text
In how many ways can n students line up if Alex and Sam must stand together?
```

### Method

Treat Alex and Sam as one block.

There are then `n - 1` objects to arrange: the block plus the other students.

Inside the block, Alex and Sam can switch places.

```text
2! · (n - 1)!
```

### Example

```text
In how many ways can 6 students line up if Alex and Sam must stand together?
```

Solution:

```text
2! · 5! = 240
```

---

# 3. Problems That Use Both Combinations and Permutations

These problems usually have two stages:

1. Choose the people or objects.
2. Arrange them, seat them, label them, or assign roles.

A helpful phrase is:

> Choose, then arrange.

---

## 3.1 Choose Students, Then Arrange Them in a Line

### Template

```text
In how many ways can r students be chosen from n students and then arranged in a line?
```

### Method

First choose the students.

```text
C(n, r)
```

Then arrange the chosen students.

```text
r!
```

Total:

```text
C(n, r) · r!
```

### Example

```text
In how many ways can 4 students be chosen from 10 students and then arranged in a line?
```

Solution:

```text
C(10, 4) · 4! = 210 · 24 = 5040
```

---

## 3.2 Choose People, Then Seat Them Around a Round Table

### Template

```text
In how many ways can r people be chosen from n people and seated around a round table?
```

### Method

First choose the people.

```text
C(n, r)
```

Then arrange the chosen people around a circle.

```text
(r - 1)!
```

Total:

```text
C(n, r) · (r - 1)!
```

### Example

```text
In how many ways can 5 people be chosen from 12 people and seated around a round table?
```

Solution:

```text
C(12, 5) · 4! = 792 · 24 = 19008
```

---

## 3.3 Choose a Committee, Then Choose Officers

### Template

```text
A committee of r is chosen from n students. Then k different officer roles are filled from the committee. How many outcomes are possible?
```

### Method

First choose the committee.

```text
C(n, r)
```

Then assign the officer roles from the committee.

```text
P(r, k)
```

Total:

```text
C(n, r) · P(r, k)
```

### Example

```text
A committee of 5 is chosen from 12 students. Then 2 different officer roles are filled from the committee. How many outcomes are possible?
```

Solution:

```text
C(12, 5) · P(5, 2) = 792 · 20 = 15840
```

---

## 3.4 Choose from Categories, Then Arrange

### Template

```text
From A objects of one type and B objects of another type, choose a objects of the first type and b objects of the second type, then arrange all chosen objects in a line.
```

### Method

Choose from each category, then arrange everyone chosen.

```text
C(A, a) · C(B, b) · (a + b)!
```

### Example

```text
From 8 freshmen and 7 sophomores, choose 2 freshmen and 3 sophomores, then arrange the chosen students in a line.
```

Solution:

```text
C(8, 2) · C(7, 3) · 5! = 28 · 35 · 120 = 117600
```

---

## 3.5 Choose Symbols, Then Make a Code

### Template

```text
A code uses 2 distinct letters chosen from L letters and 2 distinct digits chosen from D digits. The 4 symbols are then arranged in any order. How many codes are possible?
```

### Method

Choose the letters, choose the digits, then arrange all 4 chosen symbols.

```text
C(L, 2) · C(D, 2) · 4!
```

### Example

```text
A code uses 2 distinct letters chosen from 6 letters and 2 distinct digits chosen from 10 digits. The 4 symbols are then arranged in any order. How many codes are possible?
```

Solution:

```text
C(6, 2) · C(10, 2) · 4! = 15 · 45 · 24 = 16200
```

---

## 3.6 Choose Points, Then Label Them

### Template

```text
From n points, choose 3 points to form a triangle, then label the vertices A, B, and C. How many labeled triangles are possible?
```

### Method

First choose the 3 points.

```text
C(n, 3)
```

Then assign the labels A, B, and C.

```text
3!
```

Total:

```text
C(n, 3) · 3!
```

### Example

```text
From 10 points, choose 3 points to form a triangle, then label the vertices A, B, and C.
```

Solution:

```text
C(10, 3) · 3! = 120 · 6 = 720
```

---

# Student Decision Tree

Ask these questions in order.

## 1. Are we choosing a group?

If yes, use a combination.

```text
C(n, r)
```

## 2. Are we arranging, ranking, seating, labeling, or assigning roles?

If yes, use a permutation.

```text
n!, P(n, r), or a circular arrangement formula
```

## 3. Are we doing both?

If the problem says to choose first and then arrange, multiply the two counts.

```text
number of choices · number of arrangements
```

## 4. Are there categories?

Choose separately from each category and multiply.

```text
C(A, a) · C(B, b)
```

Then arrange if the problem asks for an arrangement.

## 5. Are there restrictions?

For required objects, include them first.

For forbidden objects, remove them first.

For “at least one,” consider using a complement.

## License

Copyright (c) 2026 Alan Miller.

This project is released under the **MIT License**.

See the [`LICENSE`](LICENSE) file for the full license text.
