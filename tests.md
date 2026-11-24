# Reproduce the three checks

In a fresh Codex session for each case, invoke `$research-answer-auditor` and paste only the fenced input. Compare the output with the expected verdict afterwards. The questions, proposed keys and candidate answers are practice items based on the cited public documents.

## Census resident population

```text
Use only the supplied source notes.

Question: According to the 2020 Census, how many people lived in the 50 states and the District of Columbia on April 1, 2020? Give the answer in millions to two decimal places.
Proposed key: 334.74 million.
Candidate answer: 331.45 million.

S1. U.S. Census Bureau, Table 2, closing rows (population counts). The total for residents of the 50 states and DC is 331,449,281. Puerto Rico has 3,285,874 residents. The total including Puerto Rico is 334,735,155.
S2. Census press release CB21-CN.30, opening two paragraphs. Its national resident count is 331,449,281 and covers the 50 states and DC.
```

**Expected outcome.** Revise / Incorrect / Correct. The requested population is 331,449,281. Dividing by one million and rounding gives 331.45 million. The proposed key includes Puerto Rico.

[Table 2](https://www2.census.gov/programs-surveys/decennial/2020/data/apportionment/apportionment-2020-table02.pdf) · [Press release](https://www.census.gov/newsroom/press-releases/2021/2020-census-apportionment-results.html)

## Webb image unveiling

```text
Use only the supplied source notes.

Question: On what date and at what exact minute UTC did NASA unveil Webb’s first full-color image at the White House?
Proposed key: July 11, 2022, 22:00 UTC.
Candidate answer: July 11, 2022, 22:00 UTC.

S1. NASA release 22-070, dated July 11, 2022, describes the public unveiling of the first full-color image of SMACS 0723 that Monday. The supplied excerpt gives no time.
S2. NASA Webb Mission Timeline, July 2022 entry. The first image was shown the evening of July 11, with additional targets released the next morning. This excerpt gives no minute or timezone.
```

**Expected outcome.** Hold / Unverified / Unverified. The local event date is documented. The supplied notes omit the exact UTC minute. Matching answers do not establish that detail. Request a timestamped record of the unveiling.

[NASA release 22-070](https://www.nasa.gov/news-release/president-biden-reveals-first-image-from-nasas-webb-telescope/) · [Mission timeline](https://science.nasa.gov/mission/webb/webb-mission-timeline/)

## Python stable release

```text
Use only the supplied source notes.

Question: On what date did Python 3.12.0 reach its final stable release?
Proposed key: October 2, 2023.
Candidate answer: September 19, 2023.

S1. PEP 693, release schedule for 3.12.0. Candidate 3 is dated 2023-09-19. Final is dated 2023-10-02.
S2. Python.org, Python 3.12.0 release page. The page identifies this as the stable release and dates it October 2, 2023.
```

**Expected outcome.** Accept / Supported / Incorrect. October 2, 2023 is the final release. September 19 was release candidate 3. The benchmark can be used as written.

[PEP 693](https://peps.python.org/pep-0693/) · [Python 3.12.0](https://www.python.org/downloads/release/python-3120/)

## Fresh-session checks

The three named-skill tests ran separately and were repeated after the instruction change. The revised Census run had only the portable instruction file and the example input. Its complete audit is in the README. In a separate session, a natural request to fact-check the Python answer key selected the installed skill without naming it. These checks used the same AI tool and do not measure performance across different products.
