# DOANS004 - Dự án Tetris

## Công việc tuần 2

### Trưởng nhóm (SV1)
- [x] Đưa CTDL cơ bản lên git
- [x] Phân công mỗi bạn làm 1 việc: vẽ màn hình, vẽ khối, lập trình để khối rơi xuống
- [x] Code ban đầu đã được tạo (không có hàm removeLine())
- [x] Code chỉ có: vẽ màn hình, vẽ khối, khối rơi xuống tự động (theo yêu cầu)

### Phân công công việc

#### SV2: Viết hàm removeLine()
- Cần viết hàm `removeLine()` để xóa các dòng đã đầy
- Hàm này sẽ được gọi sau khi đặt block xuống (dòng 95 trong `main()`)
- Vị trí: Dòng 70-71 trong `tetris.cpp` có comment hướng dẫn

#### SV3: Làm vuông vức viền và block
- Hiện tại block và viền hiển thị dạng hình chữ nhật (HCN) do console character
- Cần điều chỉnh để block và viền hiển thị vuông vức hơn
- Có thể cần thay đổi cách vẽ hoặc sử dụng Unicode characters

#### SV4: Viết code xoay block
- Nghiên cứu và viết code cho chức năng xoay block
- Hàm `rotate()` ở dòng 73-75 cần được implement
- Điều khiển bằng phím 'w'

#### SV5: Tăng tốc độ rơi sau khi removeLine
- Mỗi lần removeLine thì tốc độ rơi nhanh hơn
- Cần thêm biến để lưu tốc độ (hiện tại là `Sleep(200)`)
- Giảm thời gian `Sleep()` sau mỗi lần xóa dòng thành công

## Cài đặt C++ Compiler (MinGW)

**Cần cài MinGW để biên dịch code C++:**

1. **Tải MinGW:**
   - Link: https://github.com/brechtsanders/winlibs_mingw/releases/latest
   - Tải file: `winlibs-x86_64-posix-seh-gcc-*.7z`

2. **Giải nén vào `C:\mingw64`**

3. **Thêm vào PATH:**
   - `Win + R` > `sysdm.cpl` > Advanced > Environment Variables
   - System variables > Path > Edit > New
   - Thêm: `C:\mingw64\bin`

4. **Kiểm tra:**
   - Mở terminal mới: `g++ --version`

**Lưu ý:** Chỉ cần MinGW để biên dịch. Extension C/C++ trong VS Code chỉ để có IntelliSense (tùy chọn).

## Biên dịch và chạy

### Cách đơn giản nhất (Chỉ cần g++):
```bash
# Biên dịch
g++ -std=c++11 -o tetris.exe tetris.cpp

# Chạy game
tetris.exe
```

### Hoặc dùng batch file (nếu có):
```bash
compile.bat
```

**Lưu ý:** Cần cài MinGW trước. Sau khi cài MinGW và thêm vào PATH:
- Mở terminal bất kỳ
- Chạy: `g++ -std=c++11 -o tetris.exe tetris.cpp`
- Chạy: `tetris.exe`

## Điều khiển

**Lưu ý:** Code ban đầu SV1 chỉ có khối rơi xuống tự động (theo yêu cầu).
- Khối sẽ tự động rơi xuống
- Nhấn `Ctrl+C` để dừng chương trình

## Cấu trúc code

- `board[H][W]`: Mảng 2D lưu trạng thái board
- `blocks[][4][4]`: Mảng các hình dạng block Tetris
- `x, y`: Vị trí hiện tại của block đang rơi
- `b`: Chỉ số block hiện tại

## Lưu ý

- Code này chỉ chạy trên Windows (sử dụng `conio.h` và `windows.h`)
- Để chạy trên Linux/Mac, cần thay thế các hàm Windows-specific