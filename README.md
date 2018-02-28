# CD_CI_InAngular
this is a report
# Sự ra đời của Continuous Integration/Continuous Development (CI/CD)
Sự phát triển không ngừng của phần mềm đã đặt ra những thách thức không nhỏ với các lập trình viên cùng với những quy trình phần mềm truyền thống. Làm thế nào để phát triển phần mềm với một cách liên tục, mượt mà trong khi vẫn đảm bảo chất lượng sản phẩm là một yêu cầu cấp thiết. 
  => Chính vì thế Test automation và Continuous Integration/Continuous Development(CI-CD) đã ra đời, nó là một phần của giải pháp.
# Tổng quan cái nhìn về CI/CD
CI/CD được viết tắt của cụm từ : `Continuous Integration` và `Continuous Deployment`. Ban đầu Continuous Integration (Tích hợp liên tục) có nghĩa là bạn chạy “integration tests” (Là công việc kiểm thử tích hợp 1 nhóm các module riêng lẻ với nhau cùng với các Unit Test riêng lẻ trong từng module) mỗi khi code thay đổi. Trong khi Continuous Delivery (Phát hành liên tục) nghĩa là bạn tự động phát hành mọi sự thay đổi mà qua được các test. Tuy nhiên gần đây thuật ngữ CI/CD được sử dụng với một nghĩa rộng hơn để diễn tả mọi thứ liên quan đến `automation of the pipeline` từ khi một lập trình viên thêm một thay đổi vào một central repository đến khi đoạn code nằm ở production.<br>
<br>
<b> CI/CD pipeline </b> 

<b> Your code -> Commit -> Build -> Automated tests -> Deploy</b> <br>

Nhìn nhận tổng quan thì CI/CD pipeline thường gồm các bước sau:

1. Commit: Khi lập trình viên hoàn thành một thay đổi thì anh ta sẽ commit thay đổi đó vào một source code repository.
2. Build: Thay đổi được lấy ra từ repository và sau đó phần mềm được build để có thể chạy trên máy tính. Bước này phụ thuộc vào ngôn ngữ nào được dùng, đối với các ngôn ngữ phiên dịch (interpreted languages) thì bước này có thể được loại bỏ.
3. Automated tests: Đây là phần chính của CI/CD pipeline. Các thay đổi được test ở nhiều góc độ để đảm bảo nó hoạt động và không làm hại đến những phần khác. Automated tests bao gồm nhiều test suits:
  - Unit tests. Đây là phần test được chạy đầu tiên, thường là bởi các lập trình viên, dùng để test các function hoặc class. Khi những       function hoặc class này cần truy cập đến các tài nguyên bên ngoài, thì những tài nguyên đó thường được fake như là các “mock” hay         “stub”.
  - Integration tests. Là bước tiếp theo từ unit tests. Integration tests đảm bảo các module tạo nên ứng dụng hoạt động mượt mà với nhau.   Lý tưởng nhất là integration tests được chạy trong môi trường tương tự với môi trường production.
  - System tests. Test toàn bộ hệ thống trong một môi trường càng giống với môi trường production càng tốt.
4. Deploy: Phiên bản đã được build sẽ được đưa lên production.

# CI
<i>CI là Continuous Integration. Nó là phương pháp phát triển phần mềm yêu cầu các thành viên của team tích hợp công việc của họ thường xuyên, mỗi ngày ít nhất một lần. Mỗi tích hợp được "build" tự động (bao gồm cả test) nhằm phát hiện lỗi nhanh nhất có thể. Cách tiếp cận này giảm thiểu vấn đề tích hợp và cho phép phát triển phần mềm nhanh hơn.</i>

Một quá trình CI bắt đầu bằng việc người lập trình commit code lên Repository (github chẳng hạn). Bất kỳ thay đổi nào cũng sẽ tạo một vòng đời CI. Các bước trong một quá trình CI thường như sau:

  - Đầu tiên, developer commit code lên Repository.
  - CI server giám sát repo và kiểm tra xem liệu có thay đổi nào trên Repository hay không (liên tục, chẳng hạn mỗi phút 1 lần).
  - Ngay khi commit xảy ra, CI server phát hiện Repository có thay đổi, nên nó nhận code mới nhất từ Repository và sau đó build, chạy     unit và integration test.
  - CI server sẽ sinh ra các feedback (Phản hồi) và gửi đến các thành viên trong dự án.
  - CI server tiếp tục chờ thay đổi ở Repository.
  
![](https://i.imgur.com/O5Oh7FK.png)

Mỗi lần developer làm xong task, họ phải chạy một private build (tức là chạy phần mềm trên local trước), check thật cẩn thận và commit code lên Repository khi đã thấy ổn. Bước này xảy ra thường xuyên và ở bất kỳ thời điểm nào trong ngày. Việc build tích hợp sẽ không xảy ra khi những thay đổi này chưa ảnh hưởng đến repo (ví dụ: bạn commit mà chưa được merge vậy).
Chính vì vậy Developer cần build, Commit code thường xuyên để tìm ra vấn đề sớm và CI hoạt động hiệu quả nhất. 

<b>Lợi ích của việc sử dụng CI sẽ là:</b>
  - Giảm thiểu rủi ro nhờ việc phát hiện lỗi và fix sớm, tăng chất lượng phần mềm nhờ việc tự động test và inspect (đây cũng là một       trong những lợi ích của CI, code được inspect tự động dựa theo config đã cài đặt, đảm bảo coding style, chẳng hạn một function chỉ       được dài không quá 10 dòng code ...)
  - Giảm thiểu những quy trình thủ công lặp đi lặp lại (build css, js, migrate, test...), thay vì đó là build tự động, chạy test tự       động.
  - Sinh ra phần mềm có thể deploy ở bất kì thời gian, địa điểm.
  
