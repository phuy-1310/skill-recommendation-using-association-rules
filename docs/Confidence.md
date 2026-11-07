## Khái niệm

Confidence đo xác suất Y xuất hiện khi X đã xuất hiện.
Nó đơn giản là trả lời cho câu hỏi "Nếu khách hàng mua X thì khả năng họ mua Y là bao nhiêu?"

## Công thức

Confidence(X → Y) = Support(X ∪ Y) / Support(X)
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
## Ý nghĩa

Nếu một khách hàng mua Milk thì có khoảng 66.7% khả năng mua thêm Bread.
Confidence càng cao thì luật càng đáng tin cậy.
## Hạn chế
Confidence có thể bị đánh lừa khi mà Y xuất hiện quá thường xuyên.
-> X vốn không ảnh hưởng đến sự xuất hiện của Y
=> Cần sử dụng thêm [Lift](Lift.md).