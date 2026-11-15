# DFA Minimizer Simulator 🚀

An interactive, web-based educational tool designed to visualize the **DFA Minimization** process using the **Table-Filling (Myhill-Nerode) Algorithm**. 

This project provides a step-by-step visual breakdown of how a Deterministic Finite Automaton (DFA) is minimized, along with interactive state-machine graphs to prove language equivalence.

## 🌐 Live Demo
**[Click here to view the live simulator!](https://umairaalvi4843-hub.github.io/DFA-Minimizer/)**

---

## ✨ Key Features

* **Dynamic Input:** Accepts any valid DFA defined by the user (any number of states, symbols, and transitions).
* **Strict Validation:** Automatically detects and throws user-friendly errors for invalid states, symbols, or missing transitions.
* **Automated Unreachable State Removal:** Uses Breadth-First Search (BFS) to identify and strip away unreachable states before minimization.
* **Step-by-Step Table Filling:** Generates the lower-triangular pair table and includes **Prev**, **Next**, and **Auto Play** controls to walk through the algorithm round-by-round. Marked pairs (distinguishable) are highlighted in red, while unmarked pairs (equivalent) are highlighted in green.
* **Interactive Visualizations:** Utilizes the **Vis.js** library to render fully draggable and zoomable graphs of both the Original (reachable) DFA and the Minimized DFA.
* **String Validation:** A built-in tester allows users to input any string and simulate it on both the original and minimized DFAs to prove they accept/reject identical languages.

---

## 🛠️ Tech Stack

* **HTML5 & CSS3** - For the responsive, modern Dark Mode UI.
* **Vanilla JavaScript** - Houses the core logic (BFS, Table-Filling, Union-Find grouping).
* **Vis.js** - Used for rendering the interactive network graphs (nodes and edges).

---

## 🧠 Algorithm Overview

The minimization process is broken down into three main phases:

1. **Unreachable State Removal:** A BFS traversal starts from the `q0` state. Any state not visited is deleted from the automaton.
2. **Table-Filling (Myhill-Nerode):**
   * **Round 1:** All pairs `(p, q)` where one state is final and the other is not are marked with an `X`.
   * **Iterative Rounds:** For every unmarked pair `(p, q)`, if the transitions on any symbol `a` lead to a pair `(δ(p,a), δ(q,a))` that is already marked, the pair `(p, q)` is marked.
   * The loop continues until no new pairs are marked.
3. **Merging (Union-Find):** All pairs left unmarked are mathematically equivalent. The algorithm groups them into new states (e.g., `S0 = {q1, q2}`) and constructs the new minimized transition table.

---

## 🚀 How to Run Locally

Since this project uses no backend and no build tools, you can run it instantly:

1. Clone the repository:
   git clone https://github.com/umairaalvi4843-hub/DFA-Minimizer.git
2. Navigate into the folder and open `index.html` in any modern web browser (Chrome, Edge, Safari).
3. *(Optional)* If using VS Code, right-click `index.html` and select **"Open with Live Server"** for hot-reloading.

---

## 🧪 Testing & Edge Cases Handled

The simulator is designed to handle various boundary conditions without crashing:
* ✅ **All States are Final:** Merges all states into a single final state.
* ✅ **No States are Final:** Merges all states into a single non-final state (empty language).
* ✅ **Already Minimal DFA:** Correctly identifies that no states can be merged.
* ✅ **Single-State DFA:** Bypasses the table loop and renders the single node.
* ✅ **Unreachable Final States:** Stripped away before processing.