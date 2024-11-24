Các kiến thức củng cố về: Single Responsibility Principle (SRP), Cohesion, Coupling

1. Single Responsibility Principle (SRP)
SRP tuyên bố rằng mỗi lớp, module, hoặc hàm trong một hệ thống chỉ nên có một lý do duy nhất để thay đổi.

Nguyên tắc này nhấn mạnh rằng mọi thành phần của mã nguồn nên được thiết kế để chỉ xử lý một trách nhiệm duy nhất.

Trong giải pháp cho Bank Statement Analyzer, mỗi lớp như BankTransaction, TransactionParser, và các lớp xử lý khác đều có một trách nhiệm cụ thể. Ví dụ:

BankTransaction chỉ lưu trữ và quản lý thông tin về giao dịch đơn lẻ.

TransactionParser chỉ tập trung vào việc đọc và phân tích dữ liệu từ file CSV.

Việc phân chia như vậy giúp cho các lớp dễ dàng được kiểm tra, bảo trì và mở rộng mà không làm ảnh hưởng đến các thành phần khác trong hệ thống.

2. Cohesion
   
Cohesion đo lường mức độ liên kết giữa các hoạt động bên trong một thành phần. 

Một lớp hay module có độ liên kết cao khi tất cả các phần của nó đều thực hiện các nhiệm vụ liên quan chặt chẽ với nhau.

Trong ngữ cảnh của Bank Statement Analyzer, lớp BankTransaction thể hiện tính cohesion cao vì nó chỉ liên quan đến thông tin một giao dịch ngân hàng. 

Tất cả các phương thức trong lớp này đều phục vụ cho việc quản lý và xử lý thông tin giao dịch, từ đó cải thiện tính rõ ràng của mã nguồn và giảm thiểu sự phức tạp khi sử dụng lớp đó.

3. Coupling

Coupling đo lường mức độ phụ thuộc giữa các module khác nhau. 

Một hệ thống tốt thường mong muốn có độ kết nối thấp giữa các thành phần, tức là sự thay đổi trong một module ít nhất có ảnh hưởng đến các module khác.

Trong giải pháp này, việc sử dụng giao diện và lớp cụ thể (như TransactionParser và BankTransaction) giúp giảm thiểu độ phụ thuộc giữa các thành phần. 

Ví dụ, nếu cần thay đổi cách thức phân tích file CSV, chúng ta có thể sửa đổi TransactionParser mà không ảnh hưởng đến cách thức xử lý giao dịch trong BankTransaction.

Điều này làm cho chương trình ít bị ảnh hưởng bởi các thay đổi bên ngoài và dễ dàng hơn trong việc mở rộng hoặc thay thế các phần tử trong hệ thống mà không cần phải điều chỉnh mọi thành phần.

Biểu đồ UML:

Class:
![Diagram](https://www.planttext.com/api/plantuml/png/b99BJiCm48RtESKiKwcvG5HLBMK94b8hzeDZWeLZHvx9WY9Ene8ZSGNyI5MB6gbuOSdp-EQV6Nz_Vcs8qV4qw4fe988RDAy7XuPGiB86tYlmfu4EMRPmw-_PW8ET3BVGsUb9duoT9E7K639RsBDJfeyUW5voIAuN6IHQjv4Jx1afnPzXmJtZFgfPQQRo0Hr9Dsi56CDpjt-idvMMfqHFk5F4gryDhel0hK7zTioGNix1CkgQpq7q1x7GIkRUnNQlm2nXi8PVMb265_7EjOnPA5s74sbX2LUUHIeW_89wwzHH_hU81z_Zk4eJNvPZuiGlbzSqwulFru9mqekXghIRSWOcDrKRQRhmhty0003__mC0)

Uses Case:

![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aK9eSMeH5nU8LD3LjLFG24fDJ548AKhCAmRAP-Rd5MiYIJedvYINvYIMf2g4v9Savg18vPVcbU3Kw9QP1pGrlm2FoIMfwVb5cLMf2i45gNafcNdfcbmEG0R8fG00003__mC0)

Activity:

![Diagram](https://www.planttext.com/api/plantuml/png/L8un3i8m34NtdCBdA4j5gsv8gAtOhSOg4SQ9OcU0gp5m9Av0sWcsh_-UllxdzMxLC5kvizk3QqP23qDWWcww75npngm4FHg2HJYYtEQCehXOY59vXxmKHYEOeo5lJInYy6Cf185J5BjMEWJnLKr_mhvZjCOSdWHJ8l51rjhsGHFZ0qRImbOzjPXSM_bs-Gi00F__0m00)

Giải thích cách tác giả sử dụng để giải quyết các vấn đề về: SRP, cohesion, coupling:

1. Single Responsibility Principle (SRP)

SRP là nguyên tắc cho rằng mỗi lớp nên chỉ có một lý do để thay đổi, hay nói cách khác, mỗi lớp nên chỉ đảm nhận một trách nhiệm riêng.

Trong mã của chúng ta, SRP đã được áp dụng thông qua việc chia chương trình thành ba lớp khác nhau:

BankTransaction: Chịu trách nhiệm lưu trữ thông tin về một giao dịch (ngày, số tiền, mô tả).

TransactionParser: Chịu trách nhiệm đọc và phân tích dữ liệu từ file CSV để tạo ra danh sách các BankTransaction. Lớp này chỉ tập trung vào việc xử lý các file đầu vào và không chứa logic ứng dụng khác.

TransactionAnalyzer: Chịu trách nhiệm thực hiện các phép toán phân tích trên danh sách giao dịch, như tính tổng số tiền giao dịch và đếm số lượng giao dịch trong một tháng nhất định.

Bằng cách tách biệt các chức năng này thành các lớp riêng biệt, tác giả đã đảm bảo rằng mỗi lớp chỉ có một trách nhiệm duy nhất, giúp tăng cường khả năng bảo trì và mở rộng trong tương lai.

2. Cohesion

Cohesion đề cập đến mức độ mà các phần phức tạp của một lớp hoặc module tương tác với nhau để thực hiện một công việc duy nhất. Trong thiết kế của chúng ta, mỗi lớp đều có high cohesion:

BankTransaction: Tất cả các phương thức và thuộc tính trong lớp này đều liên quan đến một giao dịch ngân hàng, như ngày, số tiền, và mô tả. Điều này làm cho lớp có mức độ tập trung cao và dễ hiểu.

TransactionParser: Lớp này tập trung hoàn toàn vào việc phân tích dữ liệu từ file, không chứa bất kỳ logic nào liên quan đến việc phân tích giao dịch. Tất cả các phương thức đều liên quan đến hoạt động đọc và phân tích file.

TransactionAnalyzer: Tương tự, lớp này chỉ xử lý các phép toán phân tích dữ liệu giao dịch. Mọi phương thức ở đây đều hướng tới việc tính toán và phân tích kết quả.

Tất cả các lớp đều có mục tiêu rõ ràng và giữ cho các chức năng của nó liên kết chặt chẽ, do đó đạt được sự gắn kết cao.

3. Coupling

Coupling mô tả mức độ phụ thuộc giữa các lớp trong một hệ thống. Trong thiết kế này, tốc độ thấp về coupling đã được đảm bảo:

Các lớp trong chương trình tương tác với nhau thông qua các đối tượng chứ không phải thông qua các thuộc tính trực tiếp. 

Ví dụ:

TransactionParser tạo ra danh sách các BankTransaction, nhưng không biết gì về cách mà TransactionAnalyzer sử dụng chúng.

TransactionAnalyzer nhận vào danh sách các giao dịch mà không cần biết lớp TransactionParser đã tạo ra danh sách này như thế nào.

Điều này có nghĩa là nếu cần thay đổi logic trong lớp TransactionParser hoặc TransactionAnalyzer, điều đó sẽ không ảnh hưởng đến các lớp khác. Sự giảm thiểu coupling này giúp cho hệ thống dễ dàng bảo trì và mở rộng.
