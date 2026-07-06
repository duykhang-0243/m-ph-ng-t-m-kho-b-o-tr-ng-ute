# UTE Treasure Pathfinder AI

## Thông tin đề tài

* Trường: Đại Học Công Nghệ Kỹ Thuật TP.HCM
* Khoa: Công Nghệ Thông Tin
* Học phần: Trí Tuệ Nhân Tạo
* Mã lớp học phần: ARIN330585_08
* Giảng viên hướng dẫn: TS. Phan Thị Huyền Trang
* Sinh viên thực hiện: Thái Nhựt Huy và Ngô Duy Khang
* Đề tài: Xây dựng chương trình mô phỏng trực quan các thuật toán Trí tuệ nhân tạo trong nhiệm vụ tìm kho báu UTE

## Giới thiệu

UTE Treasure Pathfinder AI là chương trình mô phỏng trực quan quá trình tìm đường đến kho báu trên bản đồ UTE. Dự án áp dụng nhiều thuật toán Trí tuệ nhân tạo để tìm đường, vượt qua các hầm ngục phụ và minh họa cách thuật toán hoạt động trong từng tình huống cụ thể.

Mục tiêu của chương trình là giúp người dùng quan sát trực tiếp quá trình duyệt node, chọn đường đi, tính chi phí và mô phỏng nhân vật di chuyển theo kết quả của thuật toán.

## Chức năng chính

* Hiển thị bản đồ chính dưới dạng đồ thị gồm các node và cạnh.
* Cho phép chọn thuật toán tìm kiếm để tìm đường đến kho báu.
* Mô phỏng nhân vật di chuyển theo đường đi thuật toán tìm được.
* Bắt buộc đi qua các hầm ngục phụ trước khi đến kho báu.
* Hiển thị thông tin kết quả như đường đi, số node đã duyệt, chi phí và thời gian chạy.
* Có các màn chơi phụ để minh họa thêm những nhóm thuật toán AI khác nhau.

## Công nghệ sử dụng

* Python 3.10+
* HTML
* CSS
* JavaScript
* Python HTTP Server

## Các thuật toán được áp dụng

### Bản đồ chính

* Breadth-First Search
* Depth-First Search
* Iterative Deepening Search
* Uniform Cost Search
* Greedy Best-First Search
* A* Search
* Beam Search
* Hill Climbing
* Simulated Annealing

### Hầm ngục phụ

* DUN02: Backtracking kết hợp Forward Checking.
* HGL02: Belief State Search và AND-OR Search trong môi trường không quan sát đầy đủ.
* FB04: Belief State kết hợp BFS.
* Final Boss: Minimax kết hợp Alpha-Beta Pruning để mô phỏng tình huống đối kháng.

## Cách chạy chương trình

Yêu cầu: máy đã cài Python 3.10 trở lên.

Chạy lệnh sau trong thư mục chứa project:

```bash
python app.py
```

Sau đó mở trình duyệt và truy cập:

```text
http://127.0.0.1:8010
```

## Cách sử dụng

1. Mở chương trình trên trình duyệt.
2. Chọn thuật toán muốn mô phỏng.
3. Nhấn nút chạy để thuật toán bắt đầu tìm đường.
4. Quan sát quá trình duyệt node và đường đi của nhân vật.
5. Khi gặp hầm ngục phụ, chương trình sẽ chuyển sang màn mô phỏng thuật toán tương ứng.
6. Hoàn thành các hầm ngục phụ để tiếp tục nhiệm vụ tìm kho báu.

## Kết quả hiển thị

Sau khi chạy thuật toán, chương trình hiển thị các thông tin chính:

* Thuật toán được chọn.
* Trạng thái tìm được hoặc không tìm được đường đi.
* Danh sách node trên đường đi.
* Số node đã duyệt.
* Tổng chi phí đường đi.
* Thời gian thực thi.

## Tác giả

* Thái Nhựt Huy
* Ngô Duy Khang
