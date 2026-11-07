## Khái niệm

Support đo tần suất xuất hiện của một itemset trong toàn bộ tập giao dịch.
Nó đơn giản là trả lời cho câu hỏi "Tập mục này có phổ biến hay không?"
## Công thức

Support(X) = Số giao dịch chứa X / Tổng số giao dịch
## Ví dụ

Dataset:
T1 = {Milk, Bread}
T2 = {Milk, Eggs}
T3 = {Milk, Bread, Eggs}
T4 = {Bread, Eggs}

Itemset:
{Milk}

Xuất hiện ở:
- T1
- T2
- T3
=> 3 giao dịch trên tổng 4 giao dịch
Support({Milk}) = 3/4 = 0.75
## Ý nghĩa

- Support cao → itemset xuất hiện thường xuyên
- Support thấp → itemset hiếm gặp
Trong Apriori, itemset có support thấp thường bị loại bỏ sớm.
