# 🎯 AGT Auto-Bidding Competition

## Welcome Students!

This is your competition package for the AGT 2025-2026 Auto-Bidding Challenge. Design an autonomous bidding agent that competes in repeated second-price auctions to maximize utility!

## 🚀 Quick Start

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Read the guides:**
   - Start with [START_HERE.md](START_HERE.md)
   - Full guide: [STUDENT_GUIDE.md](STUDENT_GUIDE.md)
   - Quick reference: [QUICK_REFERENCE.md](QUICK_REFERENCE.md)

3. **Create your agent:**
   ```bash
   mkdir teams/my_team
   cp AGENT_TEMPLATE.py teams/my_team/bidding_agent.py
   ```

4. **Test your agent:**
   ```bash
   python simulator.py --your-agent teams/my_team/bidding_agent.py --num-games 10
   ```

## 📋 Competition Overview

### Game Structure
- **Items**: 20 total per game, 15 rounds of auctions
- **Budget**: 60 units per game
- **Auction Type**: Second-price sealed-bid (Vickrey)
- **Goal**: Maximize utility = (Values Won) - (Prices Paid)

### Tournament Structure
- **Stage 1**: Qualification arenas (5 teams each)
- **Stage 2**: Championship with top teams
- **Scoring**: Total utility across 5 games per stage

## 📦 Package Contents

```
AGT_Competition_Package/
├── 📖 START_HERE.md              # Start here!
├── 📖 STUDENT_GUIDE.md           # Complete guide (15 pages)
├── 📖 QUICK_REFERENCE.md         # Quick lookup
├── 📖 STUDENT_RESOURCES.md       # Resources overview
├── 📝 AGENT_TEMPLATE.py          # Annotated template
├── 📋 agt_competition_rules.md   # Official rules
│
├── 🧪 simulator.py               # Test your agent
├── ⚙️  main.py                    # Competition system
├── 📦 requirements.txt           # Dependencies
│
├── 💡 examples/                  # Example strategies
│   ├── truthful_bidder.py
│   ├── budget_aware_bidder.py
│   ├── strategic_bidder.py
│   └── random_bidder.py
│
├── 🔧 src/                       # System code
├── 📁 teams/                     # Your work area
├── 📊 results/                   # Auto-generated
└── 📝 logs/                      # Auto-generated
```

## 🎯 Creating Your Agent

### Required Interface

Your agent must implement the `BiddingAgent` class:

```python
class BiddingAgent:
    def __init__(self, team_name: str):
        self.team_name = team_name
        # Your initialization
    
    def bidding_function(self, item_valuation, remaining_budget, 
                        round_num, total_rounds, history) -> float:
        # YOUR STRATEGY HERE
        # Return bid amount (0 to remaining_budget)
        pass
    
    def update_after_each_round(self, round_result):
        # Optional: Update strategy after each round
        pass
```

**See [AGENT_TEMPLATE.py](AGENT_TEMPLATE.py) for detailed annotated template!**

## 🧪 Testing Your Agent

### Validate Interface
```bash
python main.py --mode validate --validate teams/my_team/bidding_agent.py
```
Expected: `✓ Agent validation PASSED`

### Quick Test (10 games)
```bash
python simulator.py --your-agent teams/my_team/bidding_agent.py --num-games 10
```

### Thorough Test (50 games)
```bash
python simulator.py --your-agent teams/my_team/bidding_agent.py --num-games 50
```

### Test Against Specific Opponent
```bash
python simulator.py --your-agent teams/my_team/bidding_agent.py \
                    --opponent examples/strategic_bidder.py --num-games 20
```

### Debug Mode
```bash
python simulator.py --your-agent teams/my_team/bidding_agent.py \
                    --num-games 1 --verbose
```

## 💡 Example Strategies

Study the examples in `examples/` folder:
- **`truthful_bidder.py`** - Bids true valuation
- **`budget_aware_bidder.py`** - Budget pacing strategy  
- **`strategic_bidder.py`** - Opponent modeling
- **`random_bidder.py`** - Random baseline

Read the code to learn different approaches!

## 📋 Allowed Dependencies

✅ **Allowed:**
- Python standard library (all modules)
- `numpy`
- `scipy`

❌ **Not allowed:**
- External APIs
- File I/O
- Network access
- Other external packages

## 📖 Key Rules

### Game Parameters
- **20 items** per game, **15 rounds** of auctions
- **60 units** budget per game
- **2 seconds** timeout per bid
- **Second-price sealed-bid** auctions (winner pays 2nd-highest bid)

### Valuation Distribution
Each game you receive 20 item valuations:
- **6 high-value** items: U[10, 20]
- **4 low-value** items: U[1, 10]  
- **10 mixed-value** items: U[1, 20]

### Scoring
**Utility = (Sum of Values Won) - (Sum of Prices Paid)**

Ranking by:
1. Total utility across all games
2. Highest single-item utility (tiebreaker)
3. Most items won (tiebreaker)

**See [agt_competition_rules.md](agt_competition_rules.md) for complete rules!**

## ⚠️ Common Issues

### ❌ Agent Not Loading
- File must be named `bidding_agent.py`
- Class must be named `BiddingAgent`
- Verify all required methods exist

### ⏱️ Timeout Errors
- Function must return in < 2 seconds
- Avoid expensive loops
- Optimize your calculations

### 📦 Import Errors
- Only use: stdlib, numpy, scipy
- No other packages allowed

### 💰 Budget Issues
- Bids over budget are auto-capped
- Check remaining budget before bidding

## ✅ Pre-Submission Checklist

- [ ] File named `bidding_agent.py`
- [ ] Class named `BiddingAgent`
- [ ] Validation passes
- [ ] Tested with 50+ games
- [ ] No timeout errors
- [ ] Team names in code header
- [ ] Only allowed imports

## 🆘 Getting Help

1. Read [STUDENT_GUIDE.md](STUDENT_GUIDE.md) thoroughly
2. Check [QUICK_REFERENCE.md](QUICK_REFERENCE.md)
3. Study example agents in `examples/`
4. Review [agt_competition_rules.md](agt_competition_rules.md)
5. Ask on course forum
6. Attend office hours

## 📅 Important Dates

- **Package Release:** December 2025
- **Submission Deadline:** [TBD - Check Moodle]
- **Competition Run:** [TBD]
- **Results Announced:** [TBD]

---

## 🏆 Good Luck!

**May the best strategy win!**

Questions? Check the documentation or ask on the forum.

Ready? Start with [START_HERE.md](START_HERE.md)!

---

*AGT 2025-2026 | Hebrew University of Jerusalem*
