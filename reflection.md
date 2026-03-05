# 💭 Reflection: Game Glitch Investigator

## 1. What was broken when you started?

I found five separate bugs in the original app:
  1. The hints were wrong; e.g., it would arbitrarily say "Go LOWER!" and "Go HIGHER!" regardless of the actual secret number. For example, a guess of `-999999` might result in a "Go HIGHER!" hint when the secret number was `25`.
  2. Sometimes guesses just wouldn't be logged despite being submitted and counting as a guess.
    - Below is an example of a game where I simply entered `1` through `11` as guesses, with `11` only showing up in history after the final guess was already used up.
```json
[
  0:1
  1:2
  2:3
  3:5
  4:7
  5:9
  6:11
]
```
  3. The *displayed* number of attempts lefts only ticks down on the second guess onwards despite the first guess actually counting as an attempt. This causes the attempts to run out when `Attempts Left` shows `1` instead of attempts left showing `0`.
  4. The difficulties are wrong. The Hard difficulty is easier than Normal (it uses range 1 to 50 while Normal uses range 1 to 100).
  5. If you run out of attempts, hitting `New Game` doesn't actually reset the game aside from resetting the attempts left to `0`.

---

## 2. How did you use AI as a teammate?

I exclusively used GitHub Copilot (VS Code extension) for this projectj. I found that the AI didn't actually make any errors in my case (which was surprising), but this could be explained since Copilot automatically selected an advanced model (GPT-5.3-Codex). In fact, I had to stop it from just fixing the entire program (which I verified via testing) since I wanted to fix the bugs one at a time and not fix everything anyway.

After each edit, I'd test the app to see if the bug was fixed and to make sure no new bugs were introduced. For example, after fixing the hints, I tested by entering various guesses and verifying that the hints were correct based on the secret number.

---

## 3. Debugging and testing your fixes

I only determined a bug to be fixed after manually verifying it (i.e., I ran the app, interacted with the specific behavior I was trying to fix).

As for tests, I had Copilot write some pytest tests for me. While it initially failed (used incorrect syntax since it seemingly thought the test file was in the same working directory as the app), I just had to prompt the agent saying it was returning a failure and it fixed the test.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
