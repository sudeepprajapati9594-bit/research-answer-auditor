# Research Answer Auditor

Use this Codex skill to check a research answer key and a candidate answer against the same sources before deciding how to grade the response.

## Try a real example

This practice item uses public Census Bureau figures. The proposed key and candidate response are sample answers supplied for the audit. The source notes are paraphrases, so the example works offline.

**Input**

```text
Use only the supplied source notes.

Question: According to the 2020 Census, how many people lived in the 50 states and the District of Columbia on April 1, 2020? Give the answer in millions to two decimal places.
Proposed key: 334.74 million.
Candidate answer: 331.45 million.

S1. U.S. Census Bureau, Table 2, closing rows (population counts). The total for residents of the 50 states and DC is 331,449,281. Puerto Rico has 3,285,874 residents. The total including Puerto Rico is 334,735,155.
S2. Census press release CB21-CN.30, opening two paragraphs. Its national resident count is 331,449,281 and covers the 50 states and DC.
```

Sources: [S1 · Table 2, final rows](https://www2.census.gov/programs-surveys/decennial/2020/data/apportionment/apportionment-2020-table02.pdf) · [S2 · Census release CB21-CN.30](https://www.census.gov/newsroom/press-releases/2021/2020-census-apportionment-results.html)

**Output from a fresh Codex session using only the portable skill and the input above**

- **Decision** — Revise the answer key.
- **Key** — Incorrect. The expected answer is **331.45 million**.
- **Candidate** — Correct. It gives the resident count for the 50 states and DC on April 1, 2020, rounded to two decimal places.
- **Evidence** — In the supplied excerpt from S1, Table 2’s closing rows give 331,449,281 residents for the 50 states and DC. Dividing by 1,000,000 gives 331.449281 million, which rounds to **331.45 million**. The proposed key comes from the 334,735,155 total that includes Puerto Rico.
- **Next step** — Replace 334.74 million with 331.45 million in the key and award the candidate full credit.

[View the example output as a screenshot](preview.png)

## What changed during testing

Three separate sessions, each using a fresh public-source case, tested a wrong census key, a wrong Python release date, and a Webb unveiling time missing from the supplied evidence. The first census audit correctly identified the population but left the unit conversion implicit. The instructions now require a one-line calculation with visible rounding. They also tell the reviewer to distinguish supported and unresolved parts of a claim, as in the Webb case. All three revised verdicts matched the expected decisions. [See the test inputs and checks](tests.md).

## Install in Codex

Download and unzip this repository, or clone it. From the repository root, run the following in Terminal (macOS/Linux):

```sh
mkdir -p ~/.agents/skills
cp -R research-answer-auditor ~/.agents/skills/
```

On Windows, copy the entire `research-answer-auditor` folder into `%USERPROFILE%\.agents\skills\`. Open a fresh Codex chat, type `$research-answer-auditor`, and paste the question, proposed key, candidate answer and source notes. For a one-off run, paste the complete `SKILL.md` into a new chat with the same input.
