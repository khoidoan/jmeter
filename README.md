# jmeter
Bài tập thực hành jMeter cho sinh viên
Mục tiêu:

Giới thiệu các khái niệm cơ bản về jMeter
Hướng dẫn sinh viên cách sử dụng jMeter để thực hiện các bài kiểm tra hiệu năng đơn giản
Giúp sinh viên hiểu cách phân tích kết quả kiểm tra và đưa ra kết luận
Bài tập:

**1. Kiểm tra hiệu năng trang web**: **baomoi.com**

Trong Test Plan, thêm một Thread Group để thiết lập số lượng người dùng ảo và lượt truy cập:
Số Threads (users): 10 (số lượng người dùng đồng thời).
Ramp-Up Period (seconds): 2 (thời gian tăng dần để tất cả threads hoạt động).
Loop Count: 10 (số lần lặp lại kịch bản).

Chạy kịch bản kiểm tra và ghi lại kết quả.
![](.jemeter2.png)

Phân tích kết quả kiểm tra, bao gồm thời gian phản hồi, số lượng yêu cầu thành công, số lượng yêu cầu thất bại, v.v.
![](.jemeter3.png)
Kết luận:
  - Thời gian phản hồi trung bình (Average): Giá trị này là 700 ms, thể hiện thời gian trung bình để nhận được phản hồi từ máy chủ cho mỗi yêu cầu. Đây là chỉ số quan trọng để đánh giá tốc độ phản hồi của máy chủ. Thời gian này khá tốt nếu mục tiêu là dưới 1 giây.
  - Độ lệch chuẩn (Deviation): Giá trị này là 291, cho thấy sự phân tán của thời gian phản hồi xung quanh giá trị trung bình. Độ lệch chuẩn càng thấp thì hiệu năng càng ổn định. Trong trường hợp này, một độ lệch chuẩn 291 so với thời gian trung bình 700 cho thấy có một số biến động trong thời gian phản hồi, nhưng không quá lớn.
  - Trạng thái (Status): Tất cả các mẫu trong bảng kết quả đều hiển thị biểu tượng thành công (màu xanh lá). Điều này cho biết tất cả các yêu cầu đã được xử lý thành công mà không có lỗi nào.
  - Bytes và Sent Bytes: Các giá trị này cho thấy lượng dữ liệu được truyền tải cho mỗi yêu cầu. Dữ liệu này có thể hữu ích để đánh giá khối lượng công việc mà máy chủ phải xử lý.
  - Latency và Connect Time(ms): Các chỉ số này cho biết thời gian chờ trước khi bắt đầu nhận dữ liệu và thời gian kết nối tới máy chủ, lần lượt. Thời gian chờ trung bình cũng nằm trong khoảng thấp cho thấy hiệu suất kết nối tốt.
    
  Từ các thông tin trên, có thể kết luận rằng hiệu năng của trang web này khá tốt, với thời gian phản hồi trung bình dưới 1 giây và không có lỗi phát sinh trong quá trình thực hiện các yêu cầu. Tuy nhiên, vẫn cần theo dõi và phân tích thêm về sự biến động trong thời gian phản hồi để đảm bảo hiệu suất ổn định trong các điều kiện tải khác nhau.

2. Kiểm tra hiệu năng API:**https://openweathermap.org/**

Sử dụng jMeter để tạo một kịch bản kiểm tra mô phỏng người dùng truy cập API.
Chạy kịch bản kiểm tra và ghi lại kết quả.
![](.jemeter4.png)
![](.jemeter5.png)
  Kết luận:
 - Thời gian phản hồi trung bình (Average): Giá trị này là 3780 ms, cho thấy thời gian trung bình để nhận được phản hồi từ API là khá cao, đặc biệt khi so sánh với tiêu chuẩn phổ thông của các API nên có thời gian phản hồi dưới 1000 ms để đạt hiệu quả tối ưu.
  - Độ lệch chuẩn (Deviation): Giá trị này là 2707, điều này chỉ ra rằng có sự biến động lớn về thời gian phản hồi giữa các lần gọi API khác nhau. Độ lệch chuẩn lớn như vậy cho thấy hiệu suất của API không ổn định.
  - Trạng thái (Status): Tất cả các mẫu trong bảng kết quả đều hiển thị biểu tượng thành công (màu xanh lá). Điều này cho biết rằng tất cả các yêu cầu đến API đã được xử lý thành công mà không có lỗi nào.
  - Latency và Connect Time (ms): Các chỉ số này đều có sự biến động, với một số thời gian chờ và thời gian kết nối khá cao (ví dụ, 868 ms và 385 ms tương ứng cho mẫu đầu tiên). Điều này cũng chỉ ra về hiệu suất kết nối chưa được tối ưu.
Kết luận chung, hiệu năng của các API được kiểm tra có vẻ không đạt yêu cầu về tốc độ phản hồi và ổn định. Cần cải thiện thời gian phản hồi và giảm biến động giữa các lần gọi để đạt được hiệu suất tốt hơn. Để cải thiện hiệu suất, có thể cần xem xét tối ưu hóa server, cải thiện cơ sở hạ tầng mạng, hoặc tối ưu hóa các truy vấn và thuật toán xử lý dữ liệu trên server.

3. So sánh hiệu năng của hai trang web hoặc API:
   
**Điểm giống nhau**
 
Trạng thái thành công: Cả hai kết quả thử nghiệm đều cho thấy tất cả các yêu cầu đều thành công với biểu tượng màu xanh lá cây.
  
**Điểm khác nhau**

   - Thời gian phản hồi trung bình:

  - baomoi.com cho thấy thời gian phản hồi trung bình là 700 ms.
  - openweathermap.org cho thấy thời gian phản hồi trung bình là 3780 ms, đáng kể cao hơn so với kết quả đầu tiên.
  - 
Độ lệch chuẩn:

  - Độ lệch chuẩn trong hình ảnh đầu tiên là 291, cho thấy mức độ biến động thấp hơn trong thời gian phản hồi.
  - Độ lệch chuẩn trong hình ảnh thứ hai là 2707, cho thấy sự biến động lớn hơn rất nhiều trong thời gian phản hồi.
Mức độ biến động trong thời gian phản hồi:

  -  baomoi.com các giá trị thời gian phản hồi dao động từ khoảng 177 ms đến 1070 ms.
  - openweathermap.org thời gian phản hồi dao động từ khoảng 911 ms đến 11899 ms, cho thấy sự không ổn định đáng kể hơn nhiều.
Kết Luận
Dựa vào so sánh này, có thể thấy rằng trang baomoi.com có hiệu năng tốt hơn nhiều so với openweathermap.org . Thời gian phản hồi trung bình thấp hơn và biến động ít hơn cho thấy nó có sự ổn định và hiệu quả cao hơn đáng kể. Hiệu suất kém hơn trong hình ảnh thứ hai có thể yêu cầu việc tối ưu hóa thêm để cải thiện thời gian phản hồi và giảm thiểu sự biến động.
