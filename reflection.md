# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

The first time I ran the app, it looked like a standard number guessing game, but it was basically impossible to win. The biggest issue was that the secret number would reset every single time I clicked the submit button, so the target was constantly moving. On top of that, the hints were completely backwards, telling me to guess higher when I was already way above the target number.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I primarily used VS Code Copilot and its Agent Mode to help restructure the project. One correct suggestion it gave was how to move the core guessing logic into logic_utils.py and update the imports in app.py so everything still talked to each other. An incorrect suggestion happened when I asked it to fix the session state; it tried to use a variable that hadn't been initialized yet, which caused a crash that I had to fix by manually adding a check to see if the key existed in the session state.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I decided a bug was truly fixed when I could play through three full games in a row without the secret number changing or the hints lying to me. I used a manual test where I looked at the "Developer Debug Info" to see the secret number, then intentionally guessed one number above and one below to verify the logic. Copilot actually helped me write a pytest case that confirmed my check_guess function returned the right strings for correct, high, and low guesses.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

I would tell a friend that Streamlit is like a script that starts from the very beginning every time you click a button or change a setting. Because of this, normal variables just get wiped out and reset to their original values constantly. You have to use Session State as a sort of "memory" for the app so it can remember things like your score or the secret number between those reruns.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One strategy I want to keep using is marking "crime scenes" in my code with # FIXME comments before I even open the AI chat. It made it much easier to point the AI to the exact line that was causing trouble. Next time, I want to be more skeptical of "Agent Mode" changes and review the file differences more closely before hitting accept, since it's easy to miss small logic errors. This project really showed me that while AI is fast at generating code, it doesn't always understand the specific way Streamlit handles state, so I still have to be the one in charge of the final logic.
