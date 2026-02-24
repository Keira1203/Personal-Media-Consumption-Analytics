# Personal-Media-Consumption-Analytics
This project analyzes my personal digital behavior using:

- YouTube watch history  
- Apple Music listening data  
- Screen time logs  
- Study time records  

The goal is to explore patterns in daily routines, media consumption, and learning habits.

## Data Sources

All raw personal data is excluded from this repository for privacy reasons.

## Tech Stack

- Python
- pandas
- matplotlib
- Jupyter Notebook

## Structure

- notebooks/: analysis notebooks  
- src/: helper functions  
- figures/: generated plots  
- data/: processed sample data only


### **Methodology** 
Monthly cycle: Data → Analysis → Prediction → Validate

## 2026/2/18
**Step 1.1**: Apple Music CSV date conversion  
`20260115` → `2026-01-15` (`pd.to_datetime(format='%Y%m%d')`)  
Extracted Jan 2026 play history → `apple_playback_2026_jan.csv` export success!

**Step 1.2**: YouTube watch-history.json analysis  
```python
df["time"] = pd.to_datetime(df["time"], format="mixed", utc=True)
jan_2026 = df[(df["time"] >= "2026-01-01") & (df["time"] < "2026-02-01")]
```

## 2026/2/19
**Step 1.1**:Apple Music CSV to the raw data file
Moved the CSV file that made yesterday to the private file

**Step 1.2**:YouTube watch-history.json
Use SQL to filter the data and find the top 10 played video

## 2026/2/23
**Apple Music**
Find the top 10 Artist and top 10 songs played.
Created the head map of the playing time due to day average the week

## 2026/2/24
**YouTube**
Get the top 10 played video with delating the promotion video from the list 
Make the API key to get the YouTube channnel from the video URL
Get the top 10 played channels
Created the head map of the playing time due to day average the week


### **Todo**

#### **Jan Analysis**
- [ ] Apple Music → SQLite database
- [ ] **Jan analysis**: 
  | Metric | SQL |
  |--------|-----|
  | Top videos | `SELECT title, COUNT(*) FROM youtube_jan2026 LIMIT 10` |
  | Time of day | `strftime('%H', time)` |
  | Play duration | `AVG(plays)` |
- [ ] Jan summary report
- [ ] Baseline prediction (Jan → Feb)
- [ ] Feb data collection start
- [ ] Screen time and study time to CSV

#### **Ongoing Monthly**
- [ ] Process new month
- [ ] Previous prediction accuracy
- [ ] Update year trend

#### **Year-End**
- [ ] Full 2026 dashboard


## Monthly Insights

### Jan 2026 Apple Music
#### TOP 10 Playes
#### Artist
| Rank | Channel | Plays |
|------|---------|-------|
| 1 | SixTONES | 138 |
| 2 | Mr.Children | 107 |
| 3 | FRUITS ZIPPER | 29 |
| 4 | ONE OK ROCK | 28 |
| 5 | RADWIMPS | 20 |
| 6 | Yuuri | 18 |
| 7 | CUTIE STREET | 17 |
| 8 | TENBLANK | 17 |
| 9 | ARASHI | 17 |
| 10 | CANDY TUNE | 12 |

#### Songs
| Rank | Song | Plays |
|------|------|-------|
| 1 | JAPONICA STYLE | 16 |
| 2 | Sign | 10 |
| 3 | Can we just be cute? | 8 |
| 4 | Anmarioboetenaiya | 8 |
| 5 | Forever Eve | 6 |
| 6 | Crystalline Echo | 5 |
| 7 | Glass Heart | 5 |
| 8 | Shirushi | 5 |
| 9 | Hatomame -Say Hello To The World.- | 5 |
| 10 | Futarigoto | 4 |

#### Play time Heatmap
![Jan Heatmap](figures/Music_weekday_hour.png)
- Friday AM peak
- Weekday PM focus
**Patterns**: Pre-weekend boost → Weekday relaxation routine

### Jan 2026 YouTube
#### TOP 10 Videos
| Rank | Video Title (English) | Views |
|------|----------------------|-------|
| 1 | [#SixTONES] Best Album "MILESixTONES -Best Tracks-"... | 10 times |
| 2 | Taiga Kyomoto - Completing the One and Only Guitar in the World - IN-PUT #3 | 7 times |
| 3 | Taiga Kyomoto - Original Electric Guitar Production - IN-PUT #1 | 7 times |
| 4 | Taiga Kyomoto - Crafting an Acoustic Guitar - IN-PUT #2 | 7 times |
| 5 | Taiga Kyomoto - WONDER LAND | 7 times |
| 6 | Taiga Kyomoto - WONDER LAND (from TAIGA KYOMOTO Anniversary...) | 7 times |
| 7 | Taiga Kyomoto - RAY (from BLUE OF LIBERTY 2025.06.18 Live...) | 7 times |
| 8 | Taiga Kyomoto - Prelude | 7 times |
| 9 | Taiga Kyomoto - LIVE DVD&Blu-ray "BLUE OF LIBERTY" OUT-PUT | 7 times |
| 10 | Taiga Kyomoto - Album "PROT.30" OUT-PUT | 7 times |


#### TOP 10 Channels
| Rank | Channel (English) | Plays |
|------|------------------|-------|
| 1 | CUTIE STREET | 28 times |
| 2 | SixTONES | 26 times |
| 3 | Mr.Children Official Channel | 18 times |
| 4 | MORE STAR | 17 times |
| 5 | Naka riisa desu | 16 times |
| 6 | Idol Daisuki Zukan (Idol Encyclopedia) | 15 times |
| 7 | Thủy Aesthetic | 12 times |
| 8 | KAWAII LAB. | 9 times |
| 9 | Kuwata Keisuke | 8 times |
| 10 | Medical Subtle Light | 8 times |

#### Play time Heatmap
![Jan Heatmap](figures/YouTube_weekday_hour.png)
- Friday AM peak
- Weekday PM focus
**Patterns**: Pre-weekend boost → Weekday relaxation routine