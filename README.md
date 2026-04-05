Data Engineering Flow:

Extraction: Raw historical cricket data harvested into Google Sheets.

Transformation: Python/Pandas scripts in Google Colab used for cleaning, handling nulls, and initial feature engineering.

Loading: Data pushed via the google-cloud-bigquery library into BigQuery for high-performance SQL analysis.

Modeling: Final "Master" tables created in SQL using CTEs and normalization to feed Looker Studio.

Data Dictionary

Core Dimensions (The "Who & When")
Player / Country: The primary identifiers for the athlete and their national team.

Career: The total span of the player's active years (e.g., 1990-2006).

Career_Start / Career_End: Integer values extracted from the career span, used for timeline analysis and cohort grouping.

Era: Categorical classification based on debut year (e.g., '90s', '10s') to compare players across different technological and pitch-condition epochs.

Longevity_Tier: A qualitative bucket (Short Peak to Iron Man) based on the total number of years active.

Batting_Style: An "Intent Index" that categorizes players (Aggressor to Blocker) based on their career Strike Rate.

Primary Metrics (The "Raw Data")
Runs / Average / Rating: Traditional performance metrics including total volume, per-innings consistency, and normalized performance ratings.

Strike_Rate: Scoring speed; used to differentiate between anchors and accelerators.

Century_Frequency: The number of innings played per century scored (lower is better).

MOM (Man of the Match): Total count of match-winning individual performances.

WinsR / WinsS: Win-specific metrics; Win-Run percentage (Runs in wins / Total runs) and Strike Rate during winning matches.

Team_Runs: The total runs scored by the player's team during their career; used to calculate relative contribution.

Advanced Calculations (The "Analysis")
wba_raw: Weighted Batting Average; a combined metric looking at a player's performance relative to both their teammates and their opposition.

Cons_Raw: A consistency coefficient that penalizes high variance and rewards steady output.

Bow_Q_Raw: A "Bowling Quality" factor that adjusts a player's score based on the strength of the bowling attacks faced in their specific era.

IPV_Raw: Independent Player Value; a "Peak Impact" metric isolating a player's performance from team context during their best years.

The Final Output
Final_GOAT_Score: A composite, weighted index (0-100) that aggregates Longevity, Peak Impact, Consistency, and X-Factor. This is the primary sorting metric for the leaderboard.
