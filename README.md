# D2R Mod - toantruyen

Bản mod tùy chỉnh dành cho **Diablo II: Resurrected** (hỗ trợ phiên bản mới nhất v3.3.93847+ và class **Warlock**).

## Tính năng chính

- **Loot Filter & Hiển thị Item**: 
  - Phân loại màu sắc rõ ràng cho Rune, Gem, Charm, Item Unique/Set.
  - Hiển thị khoảng roll của các dòng chỉ số (min-max stats).
  - Tối ưu hóa bảng tên item rơi trên mặt đất, dễ nhìn và không bị rối màn hình.
  - Hỗ trợ đầy đủ các affixes và item riêng cho class **Warlock**.
  - **Rune Cheatsheet & Phân cấp**: Hiển thị số thứ tự Rune, cấp độ (Low/Mid/High-Mid/High Rune), công thức ghép Horadric Cube và các Runeword tiêu biểu ghép từ Rune đó.
  - **Horadric Cube In-game Cheatsheet**: Bảng tra cứu trực tiếp các công thức Cube quan trọng (đục lỗ đồ trắng, sửa đồ, nâng cấp đồ Unique, craft Caster Amulet, Blood Gloves, reroll Grand Charm...).
- **Cột sáng Beacon & Âm thanh rơi đồ (Drop Sound)**:
  - Cột sáng đánh dấu Waypoint, cửa hầm chuyển map, cầu thang, rương đặc biệt (Special Chests).
  - Cột sáng riêng cho Rune, Charm, Gem quý.
  - Kích hoạt âm thanh rơi đồ (Drop chime/SFX HD) sắc nét khi Rune rơi xuống đất.
- **Direction Arrows & Bản đồ thông minh (Area Level)**:
  - Mũi tên dẫn hướng chỉ lối đi các map và nhiệm vụ.
  - Hiển thị cấp độ khu vực (Area Level) phân theo độ khó `[Normal / Nightmare / Hell]`, làm nổi bật thẻ vàng `[aLvl 85]` đối với toàn bộ các khu vực Level 85 giá trị nhất game.
- **Tối ưu đồ họa & Font chữ**:
  - Font chữ sắc nét, dễ đọc.
  - Giảm thiểu độ trễ và lag hạt hiệu ứng (VFX optimization).
  - Đã khắc phục triệt để lỗi skill/missile và quỷ triệu hồi của Warlock ở chế độ HD.

## Hướng dẫn cài đặt & sử dụng

1. Đặt thư mục `toantruyen` vào đường dẫn:
   ```
   <Thư mục cài Diablo II Resurrected>\mods\toantruyen
   ```
   *(Cấu trúc bên trong sẽ là: `...mods\toantruyen\toantruyen.mpq\data\...`)*

2. Trong **Battle.net Launcher**:
   - Chọn **Diablo II: Resurrected**.
   - Bấm vào biểu tượng Bánh răng (Cài đặt) bên cạnh nút Chơi -> chọn **Game Settings**.
   - Tích chọn ô **Additional command line arguments**.
   - Nhập vào dòng lệnh:
     ```
     -mod toantruyen -txt
     ```
   - Nhấn **Done** và khởi động game.
