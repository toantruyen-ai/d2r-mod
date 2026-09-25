# CLAUDE.md

Client-side mod cho **Diablo II: Resurrected** (build `93847`, xem `toantruyen.mpq/data/global/dataversionbuild.txt`), chơi Online Battle.net + tay cầm. README.md (tiếng Việt) mô tả tính năng cho người dùng.

## Cấu trúc

- `toantruyen.mpq/` là **thư mục** (không phải file MPQ nén). Game đọc `toantruyen.mpq/data/...` khi chạy với `-mod toantruyen`.
- `modinfo.json`: `name` phải trùng tên thư mục mod.
- File trong `data/` ghi đè file gốc cùng đường dẫn. Game chỉ load **đúng tên file** — bản nháp kiểu `item-names_xxx.json`, `- Copy.json` không có tác dụng, đừng tạo trong mod.
- `data/local/lng/strings/*.json`: bảng text (array `{id, Key, enUS, koKR, ...}`).
- `data/hd/env/porory/beacon/`: cột sáng dẫn đường (gốc từ mod porory). Mỗi `pf_beacon_*.json` ghi texture đang dùng ở dòng đầu (`// beacon_cXX_sYY_oZZ`); chỉ giữ texture được tham chiếu.
- Không có `data/global/excel/*.txt` → không cần cờ `-txt`.

## Quy ước quan trọng

- **Chỉ sửa tầng hiển thị** (strings, UI, font, SFX, model/VFX, preset đánh dấu). Không thêm excel gameplay (stats/skills/drop) — mod phải an toàn Online.
- **Slot `koKR` = Tiếng Việt.** Người chơi chọn Korean trong Battle.net để hiện tiếng Việt; `kodia.ttf` đã được thay bằng font hỗ trợ dấu tiếng Việt.
- **Tên vật phẩm/Rune giữ tiếng Anh ở cả `enUS` và `koKR`** (để trade). Chỉ Việt hóa affix, gem affix, công thức cube (`Cube:` → `Ghép:`), quest, controller hint, cảnh báo quái.
- Mã màu D2R: `ÿcN` (vd `ÿc1` đỏ, `ÿc4` vàng kim, `ÿc8` cam, `ÿc3` xanh — dùng để reset về màu xanh affix). Dòng đầu trong chuỗi item hiển thị **dưới** tên (xuống dòng `\n` in từ dưới lên), vd rune: `"ÿc0Cube: ...\nÿc1★★★★ ÿc8Ber Rune (30)"`.
- Không để `id` hoặc `Key` trùng trong một file strings (game chỉ lấy một bản, kết quả không xác định).
- Giữ BOM UTF-8 nếu file gốc có; JSON có thể chứa comment `//` ở đầu dòng. Tránh dấu phẩy thừa cuối mảng/object.

## Kiểm tra trước khi commit

```bash
python3 - <<'EOF'
import json,os,re,collections
for r,_,fs in os.walk('toantruyen.mpq/data'):
  for f in fs:
    if not f.endswith('.json'): continue
    p=os.path.join(r,f); t=open(p,encoding='utf-8-sig').read()
    try: d=json.loads(re.sub(r'^\s*//.*$','',t,flags=re.M))
    except Exception as e: print('INVALID',p,e); continue
    if '/lng/strings/' in p:
      for k in ('id','Key'):
        dup=[v for v,c in collections.Counter(x.get(k) for x in d).items() if c>1]
        if dup: print('DUP',k,p,dup[:5])
EOF
```

## Dọn dẹp

- File backup/thử nghiệm để trong `_backup/` ở root repo (đã gitignore), **không** để hậu tố `_BU` trong `toantruyen.mpq/`.
- Launch args: `-mod toantruyen` (+ `-locale koKR` cho tiếng Việt, `-locale enUS` cho tiếng Anh).
