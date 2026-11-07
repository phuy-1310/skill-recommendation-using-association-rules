## Khái niệm

Apriori là thuật toán khai phá luật kết hợp phổ biến nhất.
Ý tưởng chính:
Nếu một itemset là phổ biến (frequent itemset) thì mọi tập con của nó cũng phải phổ biến.
Ví dụ:
Nếu {Python, SQL, Power BI} là frequent itemset thì:
- {Python, SQL}
- {Python, Power BI}
- {SQL, Power BI}
- {Python}
- {SQL}
- {Power BI}
đều phải là frequent itemset.
Đây được gọi là Apriori Property.

## Quy trình hoạt động 

1. Tìm Frequent 1-itemsets
2. Sinh Candidate 2-itemsets
3. Tính Support
4. Loại các itemsets không đạt min_support
5. Lặp lại cho đến khi không sinh được itemset mới
## Ví dụ

Dataset:
T1 = {Milk, Bread}
T2 = {Milk, Eggs}
T3 = {Milk, Bread, Eggs}
T4 = {Bread, Eggs}
min_support =  50%

###### Bước 1
Frequent 1-itemsets

Milk = 3/4 = 75%
Bread = 3/4 = 75%
Eggs = 3/4 = 75%

=> Giữ lại tất cả

###### Bước 2
Candidate 2-itemsets:
{Milk, Bread}
{Milk, Eggs}
{Bread, Eggs}

Support:
{Milk, Bread} = 2/4 = 50%
{Milk, Eggs} = 2/4 = 50%
{Bread, Eggs} = 2/4 = 50%

=> Giữ lại tất cả
###### Bước 3
Candidate 3-itemset
{Milk, Bread, Eggs}

Support = 1/4 = 25% < min_support

=> Loại bỏ
Kết thúc.

## Ưu điểm

- Dễ hiểu
- Dễ triển khai
- Kết quả trực quan

## Nhược điểm

- Sinh rất nhiều candidate itemsets
- Chậm khi dữ liệu lớn
- Tốn bộ nhớ
