## Khái niệm

FP-Growth (Frequent Pattern Growth) là thuật toán khai phá luật kết hợp cải tiến từ Apriori.
Điểm khác biệt lớn nhất:
FP-Growth không sinh candidate itemsets.
Thay vào đó thuật toán xây dựng FP-Tree để lưu trữ dữ liệu một cách nén hơn.
## Ý tưởng

Apriori:
Generate Candidate
→ Tính Support
→ Loại bỏ

FP-Growth:
Xây FP-Tree
→ Khai thác trực tiếp frequent patterns
## Ví dụ

Dataset:
T1 = {Milk, Bread}
T2 = {Milk, Eggs}
T3 = {Milk, Bread, Eggs}
T4 = {Bread, Eggs}

Sau khi đếm tần suất:
Milk = 3
Bread = 3
Eggs = 3
Dữ liệu được đưa vào FP-Tree thay vì sinh nhiều candidate giống Apriori.

## Ưu điểm

- Nhanh hơn Apriori
- Không cần generate candidate itemsets
- Hiệu quả với dữ liệu lớn
- Giảm số lần quét database

## Nhược điểm

- Khó hiểu hơn Apriori
- Việc xây dựng FP-Tree phức tạp

## So sánh với Apriori

| Tiêu chí | Apriori | FP-Growth |
|-----------|-----------|-----------|
| Độ dễ hiểu | Cao | Trung bình |
| Tốc độ | Chậm hơn | Nhanh hơn |
| Candidate Generation | Có | Không |
| Dữ liệu lớn | Kém hiệu quả | Hiệu quả |
