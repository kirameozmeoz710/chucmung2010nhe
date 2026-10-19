# Hướng dẫn sửa nội dung web chúc mừng 20/10

Web này được làm để chúc mừng ngày 20/10. Tất cả lời chúc, câu hỏi, câu chữ
hiện trên web đều nằm trong **một file duy nhất**:

```
src/content.ts
```

Bạn chỉ cần mở file đó, đổi chữ, lưu lại là web tự cập nhật.
Không cần biết lập trình. Dưới đây là hướng dẫn chi tiết từng phần.

---

## 1. Đổi tên người nhận (hiện ở màn chào)

Tìm dòng gần cuối file `content.ts`:

```ts
export const RECIPIENT_NAME = '';
```

Viết tên vào giữa hai dấu nháy. Ví dụ:

```ts
export const RECIPIENT_NAME = 'Lan Anh';
```

Nếu muốn ẩn tên, để trống lại (`''`).

---

## 2. Đổi 3 câu hỏi mở đầu

Tìm phần đầu file:

```ts
export const QUESTIONS: Question[] = [ ... ];
```

Mỗi câu hỏi có dạng:

```ts
{
  prompt: 'Nội dung câu hỏi',
  hint: 'Gợi ý nhỏ (có thể để trống "")',
  options: ['Đáp án A', 'Đáp án B', 'Đáp án C', 'Đáp án D'],
  correctIndex: 1,   // số thứ tự đáp án đúng, bắt đầu từ 0
},
```

**Lưu ý quan trọng về `correctIndex`:**
- `0` = đáp án A (đầu tiên)
- `1` = đáp án B (thứ hai)
- `2` = đáp án C (thứ ba)
- `3` = đáp án D (thứ tư)

Nếu trả lời sai, web sẽ dừng lại và yêu cầu làm lại từ đầu.

---

## 3. Đổi các lá thư treo trên cây hoa sữa

Tìm phần:

```ts
export const WISHES: Wish[] = [ ... ];
```

Mỗi lá thư có dạng:

```ts
{
  title: 'Lá thư thứ nhất',
  accent: 'petal',       // màu phong thư: 'petal' (hồng) | 'sea' (xanh biển) | 'sua' (sữa vàng)
  body: 'Dòng chúc 1.\nDòng chúc 2.',   // dùng \n để xuống dòng
  signature: 'Người gửi',
},
```

**Cách thêm 1 lá thư mới:** chép nguyên một khối `{ ... }` như trên,
dán vào sau lá thư cuối (nhớ thêm dấu phẩy `,` sau khối trước đó).
Web sẽ tự động treo thêm lá thư trên cây.

**Cách bớt lá thư:** xoá một khối `{ ... }` đi.

**Cách đổi màu phong thư:** đổi `accent` thành một trong ba giá trị:
- `'petal'` — màu hồng
- `'sea'` — màu xanh biển
- `'sua'` — màu hoa sữa (vàng ngà)

---

## 4. Đổi lời chúc trong hộp quà

Tìm phần:

```ts
export const GIFT_MESSAGE = {
  title: 'Và đây là món quà cuối cùng...',
  body: 'Nội dung lời chúc...\n(dùng \\n để xuống dòng)',
  signature: 'Hộp quà nhỏ từ trái tim mình',
};
```

Hộp quà chỉ mở sau khi đã mở **hết** các lá thư trên cây.

---

## 5. Đổi các câu chữ hướng dẫn nhỏ

Các câu chữ rải rác trên giao diện nằm ở phần dưới cùng của `content.ts`:

```ts
export const WELCOME_TITLE = '...';        // tiêu đề màn chào
export const WELCOME_SUBTITLE = '...';     // dòng phụ màn chào
export const WELCOME_ENTER = 'Bắt đầu';    // nút bắt đầu
export const QUESTIONS_INTRO = '...';      // tiêu đề phần câu hỏi
export const QUESTIONS_HINT = '...';       // gợi ý dưới câu hỏi
export const GATE_FAIL_TITLE = '...';      // câu khi trả lời sai
export const GATE_FAIL_BODY = '...';
export const GATE_FAIL_RETRY = 'Thử lại';  // nút thử lại
export const TREE_INTRO = '...';           // câu hướng dẫn ở màn cây
export const GIFT_PROMPT = '...';          // câu gợi ý mở hộp quà
export const FINAL_FAREWELL = '...';       // lời chào kết
```

---

## 6. Cách xem web

Chỉ cần lưu file lại. Web tự cập nhật, không cần làm gì thêm.

## 7. Cách khôi phục nếu sửa hỏng

Nếu vô tình làm hỏng file `content.ts`, dùng **Version History** (biểu tượng
đồng hồ ở góc trên) để khôi phục lại phiên bản trước đó.

---

## Tóm tắt nhanh

| Muốn đổi gì            | Sửa ở đâu (trong `src/content.ts`)   |
|------------------------|--------------------------------------|
| Tên người nhận         | `RECIPIENT_NAME`                     |
| 3 câu hỏi mở đầu       | `QUESTIONS`                          |
| Các lá thư trên cây    | `WISHES`                             |
| Lời chúc trong hộp quà | `GIFT_MESSAGE`                       |
| Các câu chữ hướng dẫn  | `WELCOME_*`, `TREE_INTRO`, v.v.      |

Chúc bạn chỉnh sửa vui vẻ và có một ngày 20/10 thật đẹp!
