# **Tài Liệu Báo Cáo: Phân Hệ Làm Sạch & Chuẩn Hóa Dữ Liệu Họ Tên Khách Hàng**

## **1. Phân Tích Logic & Giải Pháp Kỹ Thuật**

### **Các Bước Xử Lý Chuỗi & Chuẩn Hóa Dữ Liệu**
1. **Phân tách chuỗi gốc (Delimited String Parsing):**
   * Sử dụng phương thức `.split("-")` để bóc tách chuỗi nén `"BS.nguyen_van_hai-KHOA_TIM_MACH-08:30-PHONG_302"` thành mảng 4 phần tử chứa lần lượt: Tên Bác sĩ (có tiền tố), Chuyên khoa, Giờ khám và Phòng khám.
2. **Chuẩn hóa Tên Bác Sĩ (Title Case):**
   * Bỏ tiền tố `"BS."` bằng `.replace("BS.", "")` thu được `"nguyen_van_hai"`.
   * Thay dấu gạch dưới `_` thành khoảng trắng bằng `.replace(/_/g, " ")` thu được `"nguyen van hai"`.
   * Tách tên thành các từ bằng `.split(" ")`, duyệt qua từng từ và chuyển ký tự đầu tiên thành chữ hoa (`.slice(0, 1).toUpperCase()`) kết hợp với phần còn lại viết thường (`.slice(1).toLowerCase()`). Kết quả thu được `"Nguyễn Văn Hải"`.
3. **Chuẩn hóa Chuyên Khoa:**
   * Thay thế dấu `_` thành khoảng trắng và chuẩn hóa về dạng chữ hoa chữ cái đầu từng từ (Title Case): `"KHOA_TIM_MACH"` $\rightarrow$ `"Khoa Tim Mạch"`.
4. **Chuẩn hóa Phòng Khám:**
   * Thay thế dấu `_` bằng khoảng trắng và viết thường từ "PHONG" thành "Phòng": `"PHONG_302"` $\rightarrow$ `"Phòng 302"`.

---

## **2. Bảng Ma Trận Kiểm Thử (Test Cases)**

| Trường Hợp | Đầu Vào (Chuỗi Nén) | Bóc Tách & Chuẩn Hóa | Kết Quả Hiển Thị |
|---|---|---|---|
| **Test Case 1**<br>*(Đơn hàng ca trực gốc)* | `"BS.nguyen_van_hai-KHOA_TIM_MACH-08:30-PHONG_302"` | • Bác sĩ: `"Nguyễn Văn Hải"`<br>• Chuyên khoa: `"Khoa Tim Mạch"`<br>• Giờ khám: `"08:30"`<br>• Phòng khám: `"Phòng 302"` | `========================================`<br>`    THÔNG BÁO PHÂN CÔNG CA TRỰC BÁC SĨ`<br>`========================================`<br>`Bác sĩ đảm trách : Bác sĩ Nguyễn Văn Hải`<br>`Chuyên khoa      : Khoa Tim Mạch`<br>`Thời gian khám   : 08:30`<br>`Địa điểm         : Phòng 302`<br>`========================================` |
| **Test Case 2**<br>*(Ca trực Cấp cứu)* | `"BS.tran_thi_mai-KHOA_TAI_MUI_HONG-13:45-PHONG_105"` | • Bác sĩ: `"Trần Thị Mai"`<br>• Chuyên khoa: `"Khoa Tai Mũi Họng"`<br>• Giờ khám: `"13:45"`<br>• Phòng khám: `"Phòng 105"` | `========================================`<br>`    THÔNG BÁO PHÂN CÔNG CA TRỰC BÁC SĨ`<br>`========================================`<br>`Bác sĩ đảm trách : Bác sĩ Trần Thị Mai`<br>`Chuyên khoa      : Khoa Tai Mũi Họng`<br>`Thời gian khám   : 13:45`<br>`Địa điểm         : Phòng 105`<br>`========================================` |