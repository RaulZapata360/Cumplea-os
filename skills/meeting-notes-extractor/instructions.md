# Meeting Notes & Action Item Extractor

Automatically processes meeting transcripts (Zoom, Teams, Google Meet) and creates professional meeting minutes in Word format. Extracts action items with owners, key decisions, and discussion summary.

## When to Use

- User uploads Zoom/Teams/Meet transcript
- Needs to extract action items or tasks from a meeting discussion
- Wants structured Word document shareable with the team

## How to Trigger

```
"Extract action items from this Zoom meeting transcript"
[Paste or attach transcript]
```

## Implementation

**Required library:** `python-docx`

```python
from docx import Document
from docx.shared import Inches, Pt, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
import re
from datetime import datetime

# Read transcript
with open('team_meeting_transcript.txt', 'r') as f:
    transcript = f.read()

# Keywords used to detect action items and decisions from the transcript
action_keywords  = ['action item', 'todo', 'follow up', 'will do', 'assigned to', 'deadline']
decision_keywords = ['decided', 'agreed', 'conclusion', 'resolution']

# ── Document setup ────────────────────────────────────────────────────────────
doc = Document()

title = doc.add_heading('Meeting Minutes', 0)
title.alignment = WD_ALIGN_PARAGRAPH.CENTER

# ── Metadata table ────────────────────────────────────────────────────────────
doc.add_heading('Meeting Information', level=1)
table = doc.add_table(rows=4, cols=2)
table.style = 'Light Grid Accent 1'
metadata = [
    ('Date:',      datetime.now().strftime('%B %d, %Y')),
    ('Duration:',  '60 minutes'),
    ('Attendees:', 'Extract from transcript'),
    ('Type:',      'Team Standup'),
]
for idx, (key, value) in enumerate(metadata):
    table.rows[idx].cells[0].text = key
    table.rows[idx].cells[1].text = value

# ── Action Items table ────────────────────────────────────────────────────────
doc.add_heading('Action Items', level=1)
action_table = doc.add_table(rows=1, cols=4)
action_table.style = 'Medium Shading 1 Accent 1'
for idx, header in enumerate(['Action', 'Owner', 'Deadline', 'Status']):
    action_table.rows[0].cells[idx].text = header

# Populate from transcript — replace these with parsed results
actions = [
    ('Update Q4 roadmap slides',      'Sarah', '2024-06-30', 'In Progress'),
    ('Schedule customer interviews',  'Mike',  '2024-07-05', 'Not Started'),
    ('Review budget proposals',       'Team',  '2024-07-10', 'Not Started'),
]
for action, owner, deadline, status in actions:
    row = action_table.add_row()
    row.cells[0].text = action
    row.cells[1].text = owner
    row.cells[2].text = deadline
    row.cells[3].text = status

# ── Key Decisions ─────────────────────────────────────────────────────────────
doc.add_heading('Key Decisions', level=1)
decisions = doc.add_paragraph()
for decision in [
    'Approved new feature for Q3 release',
    'Budget increase of 15% for marketing',
    'Hiring 2 additional engineers',
]:
    decisions.add_run('• ').bold = True
    decisions.add_run(decision + '\n')

# ── Discussion Summary ────────────────────────────────────────────────────────
doc.add_heading('Discussion Summary', level=1)
doc.add_paragraph(
    'Team reviewed Q2 performance and discussed priorities for Q3. '
    'Main topics included product roadmap, budget allocation, and hiring plans. '
    'All attendees aligned on key deliverables.'
)

# ── Next Steps ────────────────────────────────────────────────────────────────
doc.add_heading('Next Steps', level=1)
doc.add_paragraph('1. All action item owners to provide updates by next meeting')
doc.add_paragraph('2. Schedule follow-up for budget review')
doc.add_paragraph('3. Next meeting: July 15, 2024')

# ── Save ──────────────────────────────────────────────────────────────────────
doc.save('meeting_minutes.docx')
print("Meeting minutes created: meeting_minutes.docx")
```

## Adapt to Real Transcript

Before running, parse the transcript to fill in real data:
1. Extract attendee names from speaker labels (e.g. `[John]:`, `John Smith:`)
2. Scan for `action_keywords` to populate the Action Items table with real owner + deadline
3. Scan for `decision_keywords` to populate Key Decisions
4. Summarize the remaining text for Discussion Summary
5. Ask the user to confirm meeting date, duration, and type if not in the transcript

## Tips

- Works with Zoom, Teams, and Google Meet transcript formats
- Flags items with explicit deadlines first; infers implicit ones from context
- Formats for easy sharing — output is a clean `.docx` ready to send
