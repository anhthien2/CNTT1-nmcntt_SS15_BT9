# PHẦN 1: PHÂN TÍCH BÀI TOÁN

**1. Input - Output**

-   **Input - 5 Cấp độ tài liệu:**
    -   Cấp 1 - Tuyệt mật: `API Keys, .env, Data khách hàng`
    -   Cấp 2 - Mật: `Business Plan chi tiết, Hợp đồng`
    -   Cấp 3 - Nội bộ Kỹ thuật: `Source Code, Tài liệu API`
    -   Cấp 4 - Nội bộ Thiết kế: `File Figma, Assets`
    -   Cấp 5 - Dùng chung: `Slide Pitch, Business Summary`
-   **Input - 4 Vai trò:**
    -   Ban Kỹ thuật - 3 người, Ban Thiết kế - 2 người, Ban Kinh doanh - 2 người, Nhà đầu tư - 1 người ngoài.
-   **Output mong đợi:** 1 cây thư mục 2 cấp + 1 bảng phân quyền 6 cột hoàn chỉnh, đáp ứng Tối thiểu quyền + Chống rò rỉ + Có Version History.

**2. Giải pháp**

├── 00_QuanTri_TuyetMat / (Chỉ Admin/Trưởng nhóm)
│   └── Chứa: API Keys, file .env, data khách hàng
│
├── 01_KyThuat/
│   └── Chứa: Link Github, tài liệu test API
│
├── 02_ThietKe/
│   └── Chứa: UI Figma, logo, assets
│
├── 03_KinhDoanh_Mat/
│   └── Chứa: Business Plan bản đầy đủ, hợp đồng
│
└── 04_DungChung_Collab/
    └── Chứa: Slide Pitch + Business Summary bản rút gọn để share chéo

**3. Các bước triển khai**

-   B1: Tạo Shared Drive tên `CampusPay`, tạo 5 thư mục con như trên.
-   B2: Tạo 3 Google Groups: `kythuat@`, `thietke@`, `kinhdoanh@` để add/remove người nhanh.
-   B3: Cấp quyền theo bảng dưới đây, nguyên tắc **Restricted - Tuyệt đối không bật Anyone with link** cho thư mục 00 và 03.
-   B4: Bật Version History: File nào cũng nằm trên Drive là tự có 30 ngày.
-   B5: Kiểm tra lại bằng chế độ View as... và thu hồi: Set Expiration cho nhà đầu tư.


# Phần 2. Triển khai,Chống lỗi
| Loại tài liệu | Ban KT | Ban TK | Ban KD | Nhà đầu tư | Ghi chú bảo mật |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Tuyệt mật: API Keys, .env, Data khách hàng** | No access | No access | No access | No access | **Restricted.** Chỉ Admin. Tuyệt đối cấm Anyone with link |
| **2. Business Plan chi tiết (Mật)** | Viewer | No access | Editor | No access | **Restricted.** KT chỉ xem để hiểu context, không được sửa |
| **3. Source Code, Test API** | Editor | No access | No access | No access | **Restricted.** Chỉ KT được sửa |
| **4. UI Design, Assets đồ họa** | Viewer | Editor | Viewer | No access | KT xem để code, TK là chủ sở hữu |
| **5. Slide Pitch, Business Summary (Dùng chung)** | Commenter | Commenter | Editor | **Viewer + Expiration 14 ngày** | Share bản **PDF**, không share file gốc. Bật cho phép download |

## 3. Trả lời 3 Bẫy

**Bẫy 1 - KD share Business Plan cho KT:**  
Cấp **Viewer**. Cho đọc thôi, không cho sửa. Vậy mới đúng nguyên tắc tối thiểu quyền.

**Bẫy 2 - Nhà đầu tư muốn tải PDF về nhưng không cho sửa:**  
Cấp **Viewer**, và **BẬT** cho tải xuống. Nhưng em phải share file **PDF**, đừng share file PowerPoint/Slides gốc. Viewer thì không sửa được, nhưng vẫn tải về offline được.

**Bẫy 3 - Có người nghỉ việc:**  
Vào Shared Drive > Manage Members > **Remove** người đó ra. Xong là mất quyền truy cập tất cả file ngay lập tức. Sau đó nhớ đổi lại API Keys mà người đó từng biết.
