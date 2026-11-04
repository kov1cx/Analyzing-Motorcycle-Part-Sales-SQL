**Dự án:** Phân tích doanh thu bán buôn phụ tùng xe máy (Tháng 6 - Tháng 8/2021)  
**Phạm vi:** 3 Kho hàng (`Central`, `North`, `West`) | Khách hàng bán buôn (`Wholesale`)

---

## 1. Tóm tắt kết quả phân tích (Key Findings)

Dựa trên dữ liệu doanh thu thuần ($Net\_Revenue = \sum Total - \sum Payment\_Fee$), hiệu quả kinh doanh bán buôn trong 3 tháng ghi nhận các đặc điểm then chốt:

* **Trụ cột doanh thu chính:**
  * **Engine** và **Frame & body** là hai nhóm mang lại doanh thu đột phá nhất trong quý, đạt đỉnh vào tháng 8 tại kho **Central** (Engine đạt **$9,433.48**, Frame & body đạt **$8,571.50**).
  * **Suspension & traction** duy trì dòng tiền rất ổn định ở cả 3 tháng tại hai kho Central và North (doanh thu dao động từ $3,200 đến gần $8,000/tháng).
* **Hiệu suất hoạt động phân hóa mạnh giữa các kho:**
  * **Kho Central (Trung tâm):** Đóng vai trò hạt nhân, chiếm tỷ trọng doanh thu áp đảo ở các linh kiện cơ khí nặng và giá trị cao.
  * **Kho North (Miền Bắc):** Đóng góp doanh thu lớn thứ hai, thể hiện thế mạnh nổi trội ở nhóm *Suspension & traction* ($7,985.17 vào tháng 6) và *Frame & body*.
  * **Kho West (Miền Tây):** Hiệu suất thấp nhất hệ thống. Đặc biệt, kho West **hoàn toàn không phát sinh doanh số bán buôn cho dòng sản phẩm Engine** trong suốt 3 tháng, và doanh số *Electrical system* rơi xuống mức rất thấp ($444.98 vào tháng 7).
* **Xu hướng tăng trưởng (Seasonality):**
  * Doanh thu bán buôn có xu hướng tăng tốc mạnh vào tháng 8, đặc biệt ở nhóm phụ tùng khung sườn và động cơ, cho thấy nhu cầu bảo dưỡng, sửa chữa hoặc dự trữ phụ tùng xe máy tăng cao vào cuối mùa hè.

---

## 2. Các điểm nghẽn vận hành (Operational Bottlenecks)

1. **Lệch pha năng lực lưu kho và phân phối:** Kho West đang chịu chi phí mặt bằng/vận hành nhưng danh mục bán buôn nghèo nàn, bỏ lỡ hoàn toàn dòng hàng giá trị cao nhất (Engine).
2. **Xói mòn biên lợi nhuận do chi phí thanh toán (`payment_fee`):** Với các đơn hàng bán buôn giá trị hàng nghìn USD, việc khách hàng thanh toán qua Credit Card làm phát sinh tỷ lệ phí lớn, trực tiếp làm giảm lợi nhuận ròng của công ty.
3. **Mặt hàng phụ tùng nhỏ (`Miscellaneous`) phân tán:** Doanh thu phân tán đều nhưng giá trị đơn hàng nhỏ, làm tăng chi phí bốc dỡ và xử lý đơn hàng tại kho.

---

## 3. Đề xuất giải pháp chiến lược (Actionable Solutions)

### A. Tối ưu hóa Kho vận & Quản trị Tồn kho (Logistics & Inventory)
* **Tái cấu trúc danh mục kho West:** Khảo sát nhu cầu thị trường khu vực phía Tây; nếu thị trường có nhu cầu động cơ, cần bổ sung tồn kho an toàn (Safety Stock) cho dòng *Engine*. Nếu nhu cầu bán buôn thực tế thấp, chuyển đổi kho West thành trung tâm gom hàng/bán lẻ phụ kiện nhẹ (*Miscellaneous*, *Breaking system*) để tối ưu diện tích.
* **Chiến lược phân bổ ABC (Slotting Optimization) tại Central & North:** Ưu tiên vị trí lưu trữ gần khu vực xuất nhập (Fast-picking area) cho *Engine*, *Frame & body*, và *Suspension & traction* để rút ngắn lead time xử lý đơn sỉ lớn.
* **Kế hoạch dự trữ đón đầu mùa vụ:** Thiết lập kế hoạch nhập hàng cơ khí nặng từ tháng 5–6 nhằm chủ động nguồn cung ứng cho đợt cao điểm tháng 8.

### B. Chính sách Thương mại & Giảm thiểu Chi phí Giao dịch (Finance & Commercial)
* **Ưu đãi chuyển dịch phương thức thanh toán:** Áp dụng mức chiết khấu thương mại 1% - 1.5% cho các đơn hàng bán buôn thanh toán bằng **Chuyển khoản ngân hàng (Bank Transfer)** hoặc tiền mặt, qua đó loại bỏ phí quẹt thẻ tín dụng (thường từ 2% - 3%).
* **Gói giải pháp bán chéo (Bundling Strategy):** Thiết lập chính sách bán kèm (bundle) dòng *Miscellaneous* và *Electrical system* với các đơn hàng lớn của dòng *Engine* hoặc *Frame & body* để kích cầu phụ tùng phụ trợ.
