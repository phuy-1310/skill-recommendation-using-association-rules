## Khái niệm

Lift đo mức độ liên quan thật sự giữa X và Y. 
Kiểu nó sẽ đo X và Y xuất hiện cùng nhau 1 cách có quy tắc(luật) nhiều hơn việc xuất hiện cùng nhau ngẫu nhiên bao nhiêu lần

## Công thức

Lift(X → Y) = Confidence(X → Y) / Support(Y)
## Ví dụ

Dataset:
T1 = {Milk, Bread}
T2 = {Milk, Eggs}
T3 = {Milk, Bread, Eggs}
T4 = {Bread, Eggs}

Xét luật:
{Milk} → {Bread}

Milk xuất hiện:
- T1
- T2
- T3
⇒ 3 giao dịch

Milk và Bread cùng xuất hiện:
- T1
- T3
⇒ 2 giao dịch

Confidence({Milk} → {Bread}) = 2/3 ~ 66.7%
Support(Bread) = 3/4 = 0,75

Lift({Milk} -> {Bread}) = 0,67/0,75 ~ 0.889
## Ý nghĩa

Lift < 1 (quan hệ tiêu cực)
⇒ Milk và Bread có xu hướng xuất hiện cùng nhau ít hơn mong đợi ngẫu nhiên.
Lift = 1 (không quan hệ)
Milk và Bread không có mối quan hệ đặc biệt
Lift >1 (quan hệ tích cực)
Xuất hiện cùng nhau nhiều hơn ngẫu nhiên