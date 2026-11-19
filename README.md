# Association Rule-Based Skill Recommendation

A VietJobs_IT data-mining project that studies job-role skill requirements and context-aware skill recommendations. The notebooks document data cleaning and modeling step by step.

## Problem 1 — Role + Experience → Skills

**Goal (EN).** Discover technical skills associated with a job role and experience level using Apriori and FP-Growth. Compare the rules with a frequency baseline that ranks skills by how often they appear in the same role–experience group.

**Mục tiêu (VI).** Khai phá kỹ năng chuyên môn gắn với từng nhóm vị trí và kinh nghiệm. Baseline đếm tần suất skill trong đúng nhóm role–kinh nghiệm, không lọc bằng support, confidence hay lift. Vì vậy, đây là đối chứng trực tiếp cho luật kết hợp.

### Results / Kết quả

Five-fold cross-validation. `K` is the number of top recommendations scored. The table reports mean Precision@K, Recall@K, Hit@K and NDCG@K.

| Model | P@5 | R@5 | Hit@5 | NDCG@5 | P@10 | R@10 | Hit@10 | NDCG@10 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Apriori | 0.275 | 0.328 | 0.662 | 0.407 | 0.169 | 0.362 | 0.687 | 0.394 |
| FP-Growth | 0.275 | 0.328 | 0.662 | 0.407 | 0.169 | 0.362 | 0.687 | 0.394 |
| Popularity baseline | 0.314 | 0.385 | 0.744 | 0.449 | 0.230 | 0.522 | 0.842 | 0.483 |

**Result (EN).** The role–experience popularity baseline scores higher than both association-rule models on all four quality metrics at K=5 and K=10. Apriori and FP-Growth produce the same average of about 148 rules per fold. Apriori is faster in this run; FP-Growth uses less measured Python memory.

**Kết quả (VI).** Baseline phổ biến theo role–kinh nghiệm cao hơn hai mô hình luật ở cả bốn chỉ số tại K=5 và K=10. Apriori và FP-Growth tạo trung bình khoảng 148 luật mỗi fold. Lần chạy này Apriori nhanh hơn, còn FP-Growth dùng ít bộ nhớ Python được đo hơn.

| Model | Median runtime (s) | Mean rules/fold | Median memory (MB) |
|---|---:|---:|---:|
| Apriori | 0.656 | 147.8 | 87.127 |
| FP-Growth | 1.305 | 147.8 | 4.208 |
| Popularity baseline | 1.620 | N/A | 0.680 |

Memory is measured with Python `tracemalloc`. Results and a combined chart: [summary.csv](result/problem_1/summary.csv) · [summary figure](result/problem_1/figures/summary.png).

## Problem 2 — Role + Experience + Known Skills → Next Skill

**Goal (EN).** Given a role, experience level and known skills, recommend another skill. Apriori/FP-Growth mine skill-to-skill rules within each role–experience group. The hybrid keeps rule matches first and fills remaining positions with role–experience popularity. The baseline ranks only by role–experience popularity. Test queries hide 20% of the skills in a held-out posting.

**Mục tiêu (VI).** Từ role, exp và skill đã biết, gợi ý skill tiếp theo. Bản hybrid ưu tiên luật phù hợp rồi bù danh sách còn thiếu bằng skill phổ biến trong đúng nhóm role–exp. Baseline chỉ xếp hạng theo độ phổ biến của nhóm. Mỗi truy vấn test ẩn 20% skill của tin tuyển dụng.

### Results / Kết quả

Stratified 5-fold cross-validation. `K` là số gợi ý đầu được chấm; các điểm là trung bình qua 5 fold. Xem bảng từng fold, độ lệch chuẩn và cách diễn giải trong notebook Problem 2.

| Model | P@5 | R@5 | Hit@5 | NDCG@5 | P@10 | R@10 | Hit@10 | NDCG@10 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Apriori rules | 0.115 | 0.367 | 0.477 | 0.330 | 0.070 | 0.416 | 0.519 | 0.351 |
| FP-Growth rules | 0.115 | 0.367 | 0.476 | 0.330 | 0.070 | 0.416 | 0.519 | 0.350 |
| Apriori + fallback | 0.142 | 0.483 | 0.598 | 0.403 | 0.091 | 0.597 | 0.707 | 0.446 |
| FP-Growth + fallback | 0.142 | 0.482 | 0.597 | 0.403 | 0.091 | 0.597 | 0.707 | 0.446 |
| Popularity baseline | 0.120 | 0.424 | 0.519 | 0.360 | 0.080 | 0.548 | 0.653 | 0.405 |

**Result (EN).** The Apriori hybrid improves on the popularity baseline across all four reported quality metrics at K=5 and K=10. For example, Recall@5 rises from 0.424 to 0.483, and NDCG@10 rises from 0.405 to 0.446. Recommendation coverage reaches 1.00 because popularity fills positions when rules return too few candidates. This is a measured improvement on masked-skill recovery, not proof of a real learning sequence.

**Kết quả (VI).** Mô hình hybrid Apriori cao hơn baseline phổ biến ở cả bốn chỉ số tại K=5 và K=10. Recall@5 tăng từ 0.424 lên 0.483; NDCG@10 tăng từ 0.405 lên 0.446. Coverage đạt 1.00 nhờ fallback lấp các vị trí luật chưa gợi ý được. Đây là cải thiện trên bài kiểm tra khôi phục skill bị ẩn, không chứng minh thứ tự học thực tế.

| Model | Median runtime (s) | Mean rules/fold | Median memory (MB) |
|---|---:|---:|---:|
| Apriori rules | 9.210 | 19,120.6 | 14.661 |
| FP-Growth rules | 9.441 | 19,120.6 | 15.071 |
| Apriori + fallback | 10.567 | 19,120.6 | 14.661 |
| FP-Growth + fallback | 10.743 | 19,120.6 | 15.071 |
| Popularity baseline | 1.499 | N/A | 0.679 |

Memory is measured with Python `tracemalloc`. Download the saved model: [skill_recommender.joblib](models/skill_recommender.joblib). Open [Recommendation_Demo.ipynb](notebooks/Recommendation_Demo.ipynb) to choose role, exp, known skills and K. Full results and chart: [summary.csv](result/problem_2/summary.csv) · [summary figure](result/problem_2/figures/summary.png).

## Project Structure

```text
skill-recommendation-using-association-rules/
├── data/
│   ├── raw/VietJobs_IT.csv
│   └── processed/  # cleaned jobs, skills, transactions
├── docs/           # notes on association rules and algorithms
├── notebooks/
│   ├── EDA_and_Preprocessing.ipynb
│   ├── Problem_1.ipynb
│   ├── Problem_2.ipynb
│   └── Recommendation_Demo.ipynb
├── models/skill_recommender.joblib
├── result/
│   ├── problem_1/
│   │   ├── figures/summary.png
│   │   └── summary.csv
│   └── problem_2/
│       ├── figures/summary.png
│       └── summary.csv
├── README.md
└── requirements.txt
```
