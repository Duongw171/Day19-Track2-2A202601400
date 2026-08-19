# Reflection — Lab 19

**Tên:** Nguyễn Văn Dương
**Cohort:** A20-K3
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries, kết quả cho thấy mỗi mode có thế mạnh riêng:

- **Exact queries**: BM25 (keyword) thắng — vì các từ khóa xuất hiện trực tiếp trong tài liệu, BM25 khớp chính xác theo TF-IDF mà không cần suy luận ngữ nghĩa.
- **Paraphrase queries**: Semantic (vector) thắng — query dùng từ ngữ khác nghĩa tương đương, embedding nắm bắt được ngữ nghĩa sâu hơn mà BM25 không thể khớp.
- **Mixed queries**: Hybrid (BM25 + vector + RRF) thắng — RRF kết hợp rank từ cả hai phương pháp, bù đắp điểm yếu của từng mode, cho Precision@10 tốt nhất trung bình.

**Khi không nên dùng hybrid:** (1) Corpus kỹ thuật có từ viết tắt, mã sản phẩm cần khớp chính xác → pure BM25; (2) Hệ thống yêu cầu latency cực thấp (<5 ms) → pure BM25 nhanh hơn; (3) Câu hỏi hoàn toàn ngữ nghĩa, không có từ khóa → pure vector đủ và đơn giản hơn.

---

## Điều ngạc nhiên nhất khi làm lab này

RRF (Reciprocal Rank Fusion) với công thức đơn giản `1/(k + rank)` lại cho kết quả tốt hơn hẳn so với từng phương pháp đơn lẻ — chứng minh rằng ensemble ranking không cần phức tạp mới hiệu quả.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
