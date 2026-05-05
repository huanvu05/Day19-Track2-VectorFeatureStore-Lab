# Reflection — Lab 19

**Tên:** Huan Vu
**Cohort:** A20-K1
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên tập 50 queries:
- `exact`: Keyword (BM25) và Hybrid đạt kết quả cao nhất do BM25 khớp từ khoá tuyệt đối. Vector search kém hơn do không nhạy với exact matching.
- `paraphrase`: Vector search nhỉnh hơn nhưng vẫn yếu do embedding model `bge-small-en-v1.5` chưa hỗ trợ tốt tiếng Việt.
- `mixed`: Hybrid chiến thắng tuyệt đối. Việc kết hợp bằng RRF giúp mô hình vượt qua hạn chế của mỗi phương pháp đơn lẻ, vừa bắt được chính xác từ khoá kỹ thuật, vừa nắm được ngữ nghĩa chung.

Khi nào KHÔNG dùng hybrid:
1. **Chỉ dùng pure BM25:** Khi cần tìm mã định danh (ID, mã lỗi), log hệ thống hoặc tên riêng chính xác tuyệt đối. 
2. **Chỉ dùng pure Vector:** Khi văn bản hoàn toàn không chứa keyword chung (cross-lingual search) hoặc ở những hệ thống yêu cầu độ trễ (latency) siêu thấp, cần bỏ qua chi phí của RRF và BM25.

---

## Điều ngạc nhiên nhất khi làm lab này

Sự chênh lệch lớn khi kết hợp Hybrid Search (BM25 + Vector): chỉ với RRF k=60 đã có thể bù đắp nhược điểm cực lớn của model ngôn ngữ tiếng Anh khi xử lý các truy vấn tiếng Việt.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: Không có
