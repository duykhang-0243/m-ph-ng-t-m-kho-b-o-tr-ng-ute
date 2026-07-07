<div align="center">

# UTE Treasure Pathfinder AI

**Chương trình mô phỏng trực quan các thuật toán Trí tuệ nhân tạo trong nhiệm vụ tìm kho báu UTE**

Python Backend · HTML/CSS/JavaScript Frontend · AI Search Visualization

</div>

---

## 1. Thông tin đề tài

| Nội dung | Thông tin |
|---|---|
| Trường | Trường Đại học Sư phạm Kỹ thuật Thành phố Hồ Chí Minh |
| Khoa | Công nghệ Thông tin |
| Học phần | Trí tuệ Nhân tạo |
| Mã lớp học phần | ARIN330585_08 |
| Giảng viên hướng dẫn | TS. Phan Thị Huyền Trang |
| Sinh viên thực hiện | Thái Nhựt Huy – 24110227<br>Ngô Duy Khang – 24110243 |
| Tên đề tài | Xây dựng chương trình mô phỏng trực quan các thuật toán Trí tuệ nhân tạo trong nhiệm vụ tìm kho báu UTE |

---

## 2. Giới thiệu dự án

**UTE Treasure Pathfinder AI** là một chương trình mô phỏng trực quan quá trình tìm đường đến kho báu trên bản đồ fantasy UTE. Dự án chuyển bài toán tìm đường thành một mini game AI, trong đó nhân vật bắt đầu từ **Start** và phải tìm route hợp lệ để đến **Goal**.

Điểm đặc biệt của bài toán là nhân vật **không được đi thẳng đến kho báu ngay lập tức**. Trước khi mở rương, route phải đi qua đầy đủ ba hầm ngục phụ bắt buộc:

- **DUN02**
- **HGL02**
- **FB04**

Thông qua giao diện web, người dùng có thể chọn thuật toán, quan sát quá trình duyệt node, xem đường đi cuối cùng, tổng chi phí, số node mở rộng và thời gian thực thi. Dự án giúp minh họa trực quan cách các thuật toán AI hoạt động trong cùng một môi trường bản đồ.

---

## 3. Mục tiêu của chương trình

Dự án được xây dựng nhằm:

- Mô phỏng bài toán tìm đường trên đồ thị bằng nhiều thuật toán Trí tuệ nhân tạo.
- Trực quan hóa quá trình thuật toán duyệt node, chọn hướng đi và xây dựng route.
- So sánh hiệu quả của các thuật toán dựa trên chi phí, số node mở rộng và runtime.
- Kết hợp bài toán tìm kiếm đường đi, tìm kiếm nhiều mục tiêu có ràng buộc và tìm kiếm trong môi trường không chắc chắn.
- Tạo một công cụ demo trực quan, dễ hiểu, phù hợp với mục tiêu học phần Trí tuệ Nhân tạo.

---

## 4. Chức năng chính

Chương trình hỗ trợ các chức năng sau:

- Hiển thị bản đồ UTE dưới dạng đồ thị gồm node và edge.
- Cho phép người dùng chọn thuật toán tìm kiếm để chạy mô phỏng.
- Mô phỏng nhân vật di chuyển theo route mà thuật toán tìm được.
- Bắt buộc nhân vật đi qua các hầm ngục phụ trước khi đến Goal.
- Hiển thị route, số node đã duyệt, tổng chi phí và thời gian chạy.
- Minh họa các thuật toán khác nhau trong từng màn chơi phụ.
- Hỗ trợ so sánh kết quả thực nghiệm giữa nhiều thuật toán.
- Trực quan hóa quá trình vào hầm, hoàn thành nhiệm vụ phụ và mở rương kho báu.

---

## 5. Mô hình bài toán

Bản đồ chính được biểu diễn bằng một **đồ thị vô hướng**, trong đó:

- **Node** đại diện cho các vị trí quan trọng trên bản đồ.
- **Edge** đại diện cho các đoạn đường hợp lệ giữa hai node.
- **Cost** đại diện cho chi phí di chuyển giữa các node, chủ yếu dựa trên khoảng cách.
- **Start** là node bắt đầu của nhân vật.
- **Goal** là vị trí kho báu cần đến.
- **Checkpoint bắt buộc** gồm DUN02, HGL02 và FB04.

Route hợp lệ phải có dạng tổng quát:

```text
Start → DUN02 / HGL02 / FB04 → ... → Goal
```

Trong đó, ba checkpoint bắt buộc có thể được đi theo nhiều thứ tự khác nhau. Backend sẽ thử các thứ tự checkpoint phù hợp và chọn route tốt nhất theo thuật toán đang xét.

---

## 6. Kiến trúc hệ thống

Dự án được tổ chức theo mô hình **Python Backend + Web Frontend**.

```text
Frontend HTML/CSS/JavaScript
        │
        │ Gửi yêu cầu chọn thuật toán
        ▼
Python Backend
        │
        │ Xử lý thuật toán tìm kiếm
        ▼
Graph Data
        │
        │ Node, edge, tọa độ, chi phí
        ▼
Kết quả trả về giao diện
```

### Thành phần chính

| Thành phần | Vai trò |
|---|---|
| `app.py` | Khởi chạy server, cung cấp API và điều phối các module mô phỏng |
| `graph_data.py` | Lưu dữ liệu bản đồ, node, edge, tọa độ và checkpoint |
| `search_algorithms.py` | Cài đặt các thuật toán tìm kiếm trên bản đồ chính |
| Frontend HTML/CSS/JS | Hiển thị bản đồ, control panel, route, animation và kết quả |
| Dungeon modules | Xử lý các màn chơi phụ như DUN02, HGL02, FB04 và Final Boss |

---

## 7. Công nghệ sử dụng

| Công nghệ | Mục đích |
|---|---|
| Python 3.10+ | Xử lý thuật toán, server backend và API |
| HTML | Xây dựng cấu trúc giao diện web |
| CSS | Thiết kế giao diện, bố cục và hiệu ứng trực quan |
| JavaScript | Điều khiển tương tác, gọi API và animation |
| Python HTTP Server | Chạy chương trình cục bộ trên trình duyệt |

---

## 8. Thuật toán áp dụng

### 8.1. Thuật toán trên bản đồ chính

| Nhóm thuật toán | Thuật toán | Mục đích minh họa |
|---|---|---|
| Tìm kiếm không thông tin | Breadth-First Search | Duyệt theo tầng, phù hợp tìm đường ít cạnh trong graph không trọng số |
| Tìm kiếm không thông tin | Depth-First Search | Duyệt sâu theo nhánh, minh họa chiến lược đi sâu trước |
| Tìm kiếm không thông tin | Iterative Deepening Search | Kết hợp DFS có giới hạn độ sâu và tăng dần depth |
| Tìm kiếm theo chi phí | Uniform Cost Search | Ưu tiên đường có tổng chi phí thấp nhất |
| Tìm kiếm có heuristic | Greedy Best-First Search | Ưu tiên node có vẻ gần mục tiêu nhất |
| Tìm kiếm có heuristic | A* Search | Kết hợp chi phí đã đi và heuristic còn lại |
| Tìm kiếm heuristic giới hạn | Beam Search | Giữ một số lượng ứng viên tốt nhất để tăng tốc |
| Tìm kiếm cục bộ | Hill Climbing | Luôn chọn trạng thái tốt hơn, minh họa nguy cơ kẹt cục bộ |
| Tìm kiếm ngẫu nhiên | Simulated Annealing | Có thể chấp nhận bước đi xấu tạm thời để thoát cực trị cục bộ |

### 8.2. Thuật toán trong các hầm ngục phụ

| Khu vực | Thuật toán | Nhiệm vụ |
|---|---|---|
| DUN02 | Backtracking + Forward Checking | Tìm đường lấy KEY rồi mới được đến EXIT |
| HGL02 | AND-OR Search | Lập kế hoạch trong môi trường có nhiều kết quả hành động |
| FB04 | Belief State Search + BFS | Tìm đường khi tác tử không chắc chắn vị trí ban đầu |
| Final Boss | Minimax + Alpha-Beta Pruning | Mô phỏng tình huống đối kháng giữa người chơi và đối thủ |

---

## 9. Luồng hoạt động của chương trình

Quy trình chạy mô phỏng gồm các bước chính:

1. Người dùng mở chương trình trên trình duyệt.
2. Giao diện hiển thị bản đồ, node, cạnh và bảng điều khiển.
3. Người dùng chọn thuật toán muốn mô phỏng.
4. Frontend gửi yêu cầu đến backend.
5. Backend chạy thuật toán trên graph.
6. Nếu bài toán yêu cầu đi qua checkpoint, hệ thống xử lý từng đoạn route.
7. Kết quả được trả về frontend.
8. Nhân vật di chuyển theo đường đi thuật toán tìm được.
9. Khi gặp hầm ngục, chương trình chuyển sang màn mô phỏng tương ứng.
10. Sau khi hoàn thành đủ hầm ngục, nhân vật được phép đến Goal và mở kho báu.

---

## 10. Cách cài đặt và chạy chương trình

### 10.1. Yêu cầu hệ thống

Máy tính cần cài đặt:

- Python 3.10 trở lên
- Trình duyệt web hiện đại như Chrome, Edge hoặc Firefox

Kiểm tra phiên bản Python:

```bash
python --version
```

Hoặc:

```bash
python3 --version
```

### 10.2. Chạy chương trình

Di chuyển vào thư mục chứa project:

```bash
cd ute_treasure_pathfinder
```

Chạy server:

```bash
python app.py
```

Sau đó mở trình duyệt và truy cập:

```text
http://127.0.0.1:8010
```

---

## 11. Hướng dẫn sử dụng

1. Mở địa chỉ `http://127.0.0.1:8010` trên trình duyệt.
2. Quan sát bản đồ chính và các điểm nhiệm vụ.
3. Chọn thuật toán trong bảng điều khiển.
4. Nhấn nút chạy mô phỏng.
5. Theo dõi quá trình thuật toán duyệt node và chọn route.
6. Quan sát nhân vật di chuyển theo đường đi đã tìm được.
7. Khi vào hầm ngục phụ, hoàn thành nhiệm vụ thuật toán tương ứng.
8. Sau khi đi qua đủ DUN02, HGL02 và FB04, nhân vật có thể đến Goal để mở kho báu.
9. Xem bảng kết quả để so sánh chi phí, số node mở rộng và thời gian chạy.

---

## 12. Kết quả hiển thị

Sau mỗi lần chạy, chương trình hiển thị các thông tin:

| Thông tin | Ý nghĩa |
|---|---|
| Algorithm | Thuật toán được chọn |
| Found | Trạng thái tìm được hoặc không tìm được đường đi |
| Path / Route | Danh sách node trên đường đi |
| Path Length | Số node trong route |
| Total Cost | Tổng chi phí đường đi |
| Nodes Expanded | Số node thuật toán đã mở rộng |
| Runtime | Thời gian thực thi |
| Checkpoint Order | Thứ tự các hầm ngục bắt buộc mà route đi qua |

---

## 13. Kết quả thực nghiệm tiêu biểu

### 13.1. Bản đồ chính

| Thuật toán | Found | Số node route | Chi phí | Node mở rộng | Runtime (ms) | Thứ tự checkpoint |
|---|---:|---:|---:|---:|---:|---|
| BFS | Có | 92 | 3742.17 | 422 | 31.459 | FB04 → DUN02 → HGL02 |
| IDS | Có | 92 | 3742.17 | 73470 | 654.748 | FB04 → DUN02 → HGL02 |
| A* Search | Có | 97 | 3713.15 | 263 | 35.564 | FB04 → DUN02 → HGL02 |
| Simulated Annealing | Có | 92 | 3783.67 | 7328 | 205.213 | FB04 → DUN02 → HGL02 |
| Uniform Cost Search | Có | 97 | 3713.15 | 482 | 33.334 | FB04 → DUN02 → HGL02 |
| Greedy Best-First Search | Có | 86 | 8530.47 | 119 | 38.574 | FB04 → HGL02 → DUN02 |
| Hill Climbing | Có | 197 | 12848.27 | 200 | 6.416 | DUN02 → HGL02 → FB04 |

### 13.2. Hầm ngục phụ

| Khu vực | Thuật toán | Found | Số node route | Node mở rộng | Runtime (ms) | Mục tiêu |
|---|---|---:|---:|---:|---:|---|
| DUN02 | Backtracking + Forward Checking | Có | 36 | 66 | 0.257 | DS → KEY → EXIT |
| HGL02 | AND-OR Search | Có | 31 | 40 | 0.188 | H01 → H58 |
| FB04 | Belief State + BFS | Có | 15 | 15 | 0.183 | `{B01, B25, B38}` → B55 |

> Runtime chỉ mang tính tham khảo vì phụ thuộc vào môi trường chạy, cấu hình máy và trạng thái hệ thống tại thời điểm thực nghiệm.

---

## 14. Nhận xét kết quả

Từ kết quả thực nghiệm, có thể rút ra một số nhận xét:

- **BFS** và **IDS** tìm được route giống nhau, nhưng IDS mở rộng nhiều node hơn do phải lặp lại DFS theo nhiều giới hạn độ sâu.
- **A*** cho kết quả cân bằng tốt giữa tổng chi phí và số node mở rộng nhờ sử dụng heuristic khoảng cách Euclid.
- **UCS** có chi phí tốt tương đương A*, nhưng mở rộng nhiều node hơn do không dùng heuristic định hướng.
- **Greedy** mở rộng ít node nhưng dễ chọn route có tổng chi phí cao vì chỉ quan tâm node có vẻ gần Goal.
- **Hill Climbing** chạy nhanh nhưng dễ đi theo route dài hoặc kẹt cục bộ.
- **Simulated Annealing** phù hợp để minh họa tìm kiếm ngẫu nhiên và khả năng chấp nhận bước xấu, nhưng kết quả không ổn định bằng UCS hoặc A*.
- Các hầm ngục phụ giúp mở rộng bài toán từ pathfinding thông thường sang các dạng AI phức tạp hơn như ràng buộc, belief state và lập kế hoạch điều kiện.

---

## 15. Cấu trúc thư mục tham khảo

Cấu trúc project có thể được tổ chức như sau:

```text
UTE_Treasure_Pathfinder_AI/
│
├── app.py
├── graph_data.py
├── search_algorithms.py
│
├── index.html
├── style.css
├── script.js
│
├── assets/
│   ├── images/
│   ├── maps/
│   └── animations/
│
├── modules/
│   ├── dun02.py
│   ├── hgl02.py
│   ├── fb04.py
│   └── final_boss.py
│
└── README.md
```

---

## 16. Phạm vi và giới hạn

Dự án tập trung vào mục tiêu mô phỏng và trực quan hóa thuật toán trong phạm vi học phần. Vì vậy, một số giới hạn hiện tại gồm:

- Chi phí cạnh chủ yếu dựa trên khoảng cách trên ảnh bản đồ.
- Runtime chỉ dùng để tham khảo, không phải benchmark tuyệt đối.
- Một số thuật toán cục bộ hoặc ngẫu nhiên có thể cần fallback để bảo đảm nhân vật vẫn có route di chuyển.
- Mô phỏng ưu tiên tính dễ quan sát và dễ trình bày hơn là tối ưu hiệu năng ở quy mô rất lớn.

---

## 17. Hướng phát triển

Trong tương lai, dự án có thể mở rộng thêm:

- Thêm vật cản động trên bản đồ.
- Cho phép người dùng tự chỉnh Start, Goal và checkpoint.
- Bổ sung nhiều chế độ chi phí như thời gian, rủi ro hoặc độ khó địa hình.
- Tối ưu thuật toán và cải thiện animation.
- Thêm chế độ so sánh trực tiếp nhiều thuật toán cùng lúc.
- Mở rộng Final Boss bằng các chiến lược đối kháng phức tạp hơn.
- Lưu lịch sử chạy để phục vụ phân tích và đánh giá.

---

## 18. Tác giả

| Họ và tên | MSSV |
|---|---|
| Thái Nhựt Huy | 24110227 |
| Ngô Duy Khang | 24110243 |

---

## 19. Giảng viên hướng dẫn

**TS. Phan Thị Huyền Trang**

---

<div align="center">

**UTE Treasure Pathfinder AI**  
*AI không chỉ tính toán đường đi, mà còn giúp người học nhìn thấy cách máy ra quyết định.*

</div>
