# GroupDNA - WhatsApp Chat Analyzer

**"Spotify Wrapped, but for your friend group."**

A Python tool that takes a WhatsApp chat export and turns it into a personality + activity report - who's the night owl, who's the spammer, who never replies, what words the group is obsessed with, and a personality archetype for every member.

---

## Screenshot

![GroupDNA Report Output](report_screenshot.png)

---

## What it does

It reads a raw WhatsApp `.txt` export, parses every line, and builds a formatted report with:

- **Group overview** - total messages, date range, per-person distribution
- **Activity analysis** - busiest day and busiest hour
- **NumPy heatmap** - a 6×24 matrix of who messages when, rendered as text art
- **Top words** - the group's most-used words with bar charts
- **Response patterns** - fastest and slowest repliers
- **Silent streaks** - longest consecutive days each person went quiet
- **Personality archetypes** - one of 8 archetypes assigned to every member

### Sample results (on the provided `hostel_bois.txt` dataset)

| Person | Archetype | Why |
|---|---|---|
| Rahul | THE SPAMMER | avg 4.5 msgs in a row |
| Priya | THE GROUP MOM | 61.7% caring keywords |
| Aman | THE NIGHT OWL | 79.8% msgs after 11 PM |
| Karan | THE STORYTELLER | avg 57.0 words per msg |
| Neha | THE DRAMA QUEEN | 62.2% drama msgs |
| Vikas | THE GHOST | silent on 73.3% of days |

---

## Constraints I followed

This was the whole point of the project - build something polished using **only fundamentals**.

### What I used
- Python fundamentals (variables, loops, conditionals, functions, f-strings)
- Lists, tuples, sets, dictionaries
- `open()` and file reading
- `datetime` (only `strptime` and `timedelta`)
- NumPy (`np.zeros`, indexing, slicing, `sum`, `max`, `min`)

### What I did NOT use
- ❌ pandas (no DataFrame, no `read_csv`)
- ❌ matplotlib / seaborn / plotly (no plotting library - heatmap is text-based)
- ❌ `collections.Counter` (built my own counter with a dict)
- ❌ `collections.defaultdict` (used regular dict with `.get()`)
- ❌ `re` regex (all pattern matching done with string methods)
- ❌ Any AI/ML library

---

## How to run

### Option 1: Google Colab (easiest)

1. Download `GroupDNA_Project.ipynb` and `hostel_bois.txt` from this repo
2. Go to [Google Colab](https://colab.research.google.com) and upload the notebook (**File → Upload notebook**)
3. Click the **folder icon** (📁) in the left sidebar and drag-and-drop `hostel_bois.txt` into it
4. Click **Runtime → Run all** (or press `Ctrl+F9`)

### Option 2: Local (Jupyter)

1. Clone this repo
2. Make sure you have Python 3 + NumPy + Jupyter installed
3. Run `jupyter notebook GroupDNA_Project.ipynb`
4. Run all cells top to bottom

### Option 3: Run the standalone `.py` files

Each feature is in its own file and can be run on its own:

```
python3 feature1_parser.py
python3 feature2_group_overview.py
python3 feature3_activity_analysis.py
python3 feature4_heatmap.py
python3 feature5_word_analysis.py
python3 feature6_response_silent.py
python3 feature7_archetypes.py
python3 feature8_final_report.py
```

---

## Run it on your own chat (bonus)

After it works on `hostel_bois.txt`, you can run it on a real group chat:

1. Open a WhatsApp chat → **Menu → More → Export chat** → choose **Without media**
2. Save the `.txt` file
3. Point the notebook at your file (replace `"hostel_bois.txt"` with your filename)
4. Run it and screenshot the report

⚠️ **Don't share your real chat publicly.** Only share the screenshot of the output, and ask your group members first.

---

## Project structure

```
GroupDNA/
├── GroupDNA_Project.ipynb        # The main notebook (all 8 features)
├── hostel_bois.txt               # The provided dataset (synthetic)
├── report_screenshot.png         # Screenshot of the final report
├── README.md                     # This file
├── feature1_parser.py            # Feature 1 - Chat parser
├── feature2_group_overview.py    # Feature 2 - Group overview
├── feature3_activity_analysis.py # Feature 3 - Busiest day/hour
├── feature4_heatmap.py           # Feature 4 - NumPy heatmap
├── feature5_word_analysis.py     # Feature 5 - Top words
├── feature6_response_silent.py   # Feature 6 - Response times + streaks
├── feature7_archetypes.py        # Feature 7 - Personality archetypes
└── feature8_final_report.py      # Feature 8 - Final integrated report
```

---

## Built with

Python 3 · NumPy · The Unlox Academy Minor Project (Week 1)

---

**Note:** I used AI (Claude) as a learning aid for a few parts - reviewing the multiline parser logic, fixing a silent-streak bug, and tuning the stop-word list so the group's actual slang (bhai, scene, yaar) would surface in the top words. Every number in the report comes from running the code, not from guessing.
