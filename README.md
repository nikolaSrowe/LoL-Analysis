# LoL-Analysis

## Motivation

In honour of completing Coursera's Google Data Analytics Certificate, I wanted to end it with a mini personalized project to practice my skills and also to showcase my very amazing League of Legends statistics.

A personal project should showcase my interests and give you insight on who I am as a person and no better way than to show you my own personal stats on the Rift. That's exactly what guided me to picking this topic. In my spare time I play League. After my finals, I'd play a game of League. After long days at work, I'd play League. I've grown many friendships playing and have stayed upuntil the the late hours of night to watch tournaments. Has League been worth my time? 



It's important to make some disclaimers before we continue, and these may be repeated when I touch on the limitations of this project:

I DO NOT PLAY RANKED. I don't play the game to be good, I play for fun, and if you know anything about the League community, that's not always good enough. To avoid toxic behaviour, I played only Co-op vs. AI games for the first two years because I was too scared to play with real people. Since then I've upgraded to playing Swiftplay and ARAM games only. Therefore the stats I've accumulated are basically the equivalent of playing Minecraft on peaceful mode. These may look good, but they don't reflect real gameplay or mechanics.

Insights like this are also easy to find on existing websites such as [op.gg](https://op.gg/), however I wanted to try getting my own scores instead. My personal comparison to pro stats is also just for my own amusement (I have no intention of going pro, don't worry Faker), so nothing here is meant to be taken seriously, other than my data skills :)

**Riot API note:** _This project isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing League of Legends. League of Legends and Riot Games are trademarks or registered trademarks of Riot Games, Inc._


## Tech Used

- Python (Jupyter Notebook via Google Colab)
- Libraries: pandas
- Microsoft Excel
- CSV, Workbook
- Power BI
- Tableau
- Automation: Claude


## Data Collection

This project uses my personal match data collected using the Riot Games API from the [Riot Developer Portal](https://developer.riotgames.com/apis), in accordance with Riot's API Terms and Policies. For my comparisons with Faker and Keria, professional player benchmark data is sourced from [Oracle's Elixir](https://oracleselixir.com/tools/downloads), used non-commercially for personal analysis; credit to Tim Sevenhuysen for maintaining this dataset. Game statistics referenced are the property of Riot Games, Inc.

The Excel sheet used: `2025_LoL_esports_match_data_from_OraclesElixir`

## Data Cleaning

I removed any columns that weren't relevant to the calculations/insights I wanted. Many columns in the Oracle's Elixir sheet weren't things I needed, so those were removed. Since I got to choose which information to grab from the Riot API directly, there was no cleaning needed on my own match CSV and I later converted it into a workbook to perform analysis and transformations in Excel during the analysis step. However, the workbook downloaded from Oracle's Elixir contained many metrics I wasn't concerned with, including patch info, bans/picks, dragon/baron/tower objective columns, gold/XP/CS at specific time intervals (10/15/20/25 min), and other team-level jungle/objective stats not relevant to an individual player comparison.

## Data Analysis

From my own spreadsheet, I initially analyzed summarizing my data entirely, until I realized that for a proper comparison I needed to filter by game mode. I needed to focus on a single game mode, as differences between ARAM and Summoner's Rift such as vision score, CS, and other stats, would have been skewed if I hadn't filtered.

I created several pivot tables for insight:
- Games per Champ -> number of ARAM and SR games played by each champion
- Champ Position (SR), filtered by win -> what position I win the most in
- Total Win/Loss of each champ in each game mode -> which champ I win or lose the most as
- Champ Stats -> KDA (min, average, max), overall and filtered by game mode
- Champ Vision Score -> filtered to champs only played in SR
- Win rate by day of week -> count of wins and losses each day
- Win rate by time of day -> count of wins/losses at different hours

I also wanted to find any personal habits, so I took note of which days of the week and what hours of the day my win rate is at its peak. These tables set up the visualizations and comparisons between Keria, Faker, and me.


## Findings

All finding visuals are found in [`FinalLoLStatsPowerBI.pdf`](visualization_report/FinalLoLStatsPowerBI.pdf).

I don't actively play SR as much as I do ARAM, especially with the release of Mayhem, so the stats are stretched thin. I believe the loss of familiarity also negatively impacted my scores toward the beginning of 2026. Swain and Miss Fortune are the only champs that slightly improve over time, whereas my Senna actually declines (sad, because how can I not main my main).

I compared my stats to Keria's using radar charts. The raw numbers were initially too large to compare meaningfully, so all values were normalized to a 0–100 scale, where 100 represents the highest performer per metric. Keria and I are almost exact opposites on this chart, showing how different our gameplay really is:

- **KDA:** Mine is 2.33, Keria's is 4.62; he basically doubles my score.
- **Avg Deaths:** I die 1.39x more often than Keria (4.57 vs. 3.29) which probably doesn't help my KDA either.
- **Avg Assists:** Keria almost doubles my assist count by 14.21 vs. my 7.93.
- **Kill Participation:** I'm absent from 62.9% of team fights, while Keria is present for 76.7% of his. This is our biggest gap.
- **Damage/min:** I deal a lot more than Keria; 517.2 vs. his 282.2. This shows I'm playing to deal damage, not necessarily to support.
- **CS/min:** Mine sits at 2.5, Keria's at 0.96, because I love taking your waves (you do not want me as your support).
- **Vision Score (normalized):** Keria again doubles my score with 106.8 vs. my 49.3. This comes from being too scared to bush-check and wander. Since I stay mostly in bot lane, I have limited areas to ward. This may also explain my low kill participation, since I miss fights I never roam toward.

The reason I compare more specific stats with Keria and not Faker is role difference. It makes less sense to compare my support stats to a pro mid laner's. Keria, playing the same role on the same team, is the closest fair benchmark available.

However, to keep my promise of comparing myself to Faker, I built a bar chart of the two stats that are at least semi-comparable across roles: average KDA and average deaths. Overall, I have the lowest KDA and the highest death rate of the three.

### **Personal Habits:** 
I wanted to check when my prime playing occured: what day of the week and what time of day was I cooking.
<img width="821" height="445" alt="image" src="https://github.com/user-attachments/assets/8a451324-49a3-4105-90eb-8d7ff72c4fed" />

My peak playing hours are between 9:00pm and 10:00pm. Before this I have a very low win rate, indicating that I need to warm up playing. At 11:00pm my win rate decreases again. This is because of my sleeping schedule, I actually get really tired around this time and regret accepting match.

<img width="731" height="432" alt="image" src="https://github.com/user-attachments/assets/8d3bbe29-9c5f-4535-aef3-c6b5a8a23e1e" />

Now we look at what day of the week has the highest win rate. This is done with a heatmap: Thursdays seem to be my most dominant days with both Friday and Sunday close behind. Towards the end of the week I find more energy/time to play the game. There is no strongly outstanding day.

## Files

| File | Description |
|---|---|
| [`LeagueOLegends.ipynb`](code/LeagueOLegends.ipynb) | Jupyter notebook (built in Google Colab): Python + pandas script that pulls match data from the Riot API |
| [`jackdzn_match_history.csv`](data/jackdzn_match_history.csv) | Raw match history exported from the notebook |
| [`jackdzn_match_history_MASTER.xlsx`](data/jackdzn_match_history_MASTER.xlsx) | Workbook containing the raw data sheet plus a summary sheet with pivot tables analyzing champs and stats |
| [`FinalLoLStatsPowerBI.pdf`](visualization_report/FinalLoLStatsPowerBI.pdf) | Finalized findings: all charts built in Power BI |
| [`Final_Personal_Stats_LoL_Workbook.pdf`](visualization_report/Final_Personal_Stats_LoL_Workbook.pdf) | Tableau dashboard: individual charts plus combined dashboard view of champion stats and peak performance |
| [`LoL_Habit_stats_and_more_champion_charts.pdf`](visualization_report/LoL_Habit_stats_and_more_champion_charts.pdf) | Tableau dashboard: combined view of win-rate-by-hour, day-of-week heatmap, playstyle scatter, and KDA-over-time |

## Limitations

**My data:**
- Only 42 games total; 4 were errors, 10 were ARAM (not comparable due to game mode differences). This leaves only 28 usable games,which is a pretty inefficient sample size.
- Some champs in that sample were only played once meaning if I had won one game or lost one game the win rate would have been 100% or 0%. This is also inefficient and not a comparable stat, so I filtered only some statistics to include champs that had three or more games.
- For habit stats (win rate by time of day), some time slots only had 1 game played. Again, a single win or loss there shows as 100%, which isn't meaningful. I only counted time slots with 2+ games.

**Comparisons between me and pros:**
- Casual Swiftplay vs. professional tournament play is inherently hard to compare.
- My matches averaged ~7–10 minutes shorter than pro matches, which inflates all my "per-minute" stats, which making direct comparison unreliable.
- I can't accurately compare myself to Faker directly since I play bot lane, mostly as support. Mid and bot support have different objectives, so stats like vision score and CS aren't apples-to-apples.
- This led me to compare myself against Keria instead who is a pro playing the same position, on the same team as Faker.

## Future / What I'd do differently

- Calculate how big the overall gap is between Keria/me and Faker/me
- Estimate how long, or what it would actually take, to reach pro level
- Identify what kind of training/improvement would be needed
- Ask: is support actually the right position for me?
- Identify which champs are genuinely the best fit for my playstyle
