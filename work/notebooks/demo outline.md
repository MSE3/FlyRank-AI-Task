## 1. 5-Minute Demo Outline

*For the Week-8 showcase — optional, but ready if presenting.*

**0:00–0:30 — The question**
"Which of a client's thousands of pages should an editor review first, given limited time?"

**0:30–1:30 — The method**
Built on FlyRank's real, anonymized search-performance data (30,000 pages, 32 clients). A
transparent rule-based baseline (CTR below what its search position typically earns) was
compared, on the same client-grouped test split, against four models — Logistic Regression,
Decision Tree, Random Forest, Gradient Boosting.

**1:30–3:00 — One chart**
*(Show the Precision@K bar chart.)* Every method compared on the identical held-out fold — the
baseline rule reaches 59.6% precision at the top of the queue; Gradient Boosting reaches 68.9%.

**3:00–4:00 — One honest result**
Before trusting that number: a genuine leak was found and proven, not assumed — two columns
that reconstructed the label almost exactly (correlation 0.99999) — removed before any model
was trained. A naive random split also inflated the same model's score by 12 points (0.755 vs.
the honest 0.632 ROC-AUC) — caught by testing the split itself, not just the model.

**4:00–5:00 — One recommendation**
Start the editorial queue with the `ctr_below_position_expectation` reason code — the
highest-volume, most explainable flag. Close with what should never be automated (no
auto-publishing, no auto-deleting pages) and the link to the full reproducible write-up.

---

## 2. Shareable Cuts

### Social post

> Built a content-decline scoring system on real FlyRank search data — and before trusting the
> model, I proved a data leak existed: two columns reconstructing the label almost exactly
> (correlation 0.99999). After removing them and validating with a client-grouped split (not a
> naive random one — that alone inflated the score by 12 points), a Gradient Boosting model
> still beat a transparent rule-based baseline: 68.9% vs. 59.6% precision on the pages that
> matter most. Full write-up + reproducible notebooks: [your deployed paper URL]

### Employer-facing summary (3 sentences)

I built a reason-coded scoring system that ranks which web pages are declining in search
performance and should be reviewed first, trained and validated on FlyRank's real anonymized
search-performance dataset (30,000 pages across 32 clients). Using a client-grouped validation
split — and after catching and removing a genuine data leak I discovered myself through direct
testing, not assumption — the model beat a transparent rule-based baseline by 9 points of
precision (68.9% vs. 59.6%) at flagging real decliners in the top 10% of a review queue. The
result ships as an honest, human-reviewed action playbook rather than a black box: every
flagged page carries a plain-English reason, and a clear list defines what should never be
automated.
