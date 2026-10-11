# browser-cores

Kho lưu trữ core trình duyệt do Multilogin phát hành: Chromium tuỳ biến **Mimic** và Firefox tuỳ biến **Stealthfox**. Các gói không ký code và không phải mã nguồn MintMultiX. Repo này chỉ chứa file `README.md` + `SHA256SUMS`; toàn bộ gói nằm trong release cuốn chiếu [`browser-cores`](https://github.com/OmniMintX/browser-cores/releases/tag/browser-cores) (asset được thêm dần, không gắn với phiên bản app).

Bản sao của release cùng tên trên `OmniMintX/MintMultiX`.

## Tải và kiểm tra checksum

```sh
gh release download browser-cores --repo OmniMintX/browser-cores \
  --pattern 'mimic_154.2-darwin-arm64.tar.gz' --pattern SHA256SUMS
shasum -a 256 -c --ignore-missing SHA256SUMS
```

`SHA256SUMS` trong repo (nhánh `main`) và trên release là cùng một file: 64 dòng cho 64 gói `.tar.gz`.

## Hai loại gói (thứ tự ưu tiên)

| Loại | Tên asset | Nguồn | Nội dung |
|---|---|---|---|
| **Gốc Multilogin (mặc định)** | `<browser>_<ver>-<os>-<arch>.tar.gz` | tarball gốc từ CDN Multilogin | `adapter.bin` (Windows: `adapter.exe`) và file trình duyệt nằm **ngay ở gốc** archive — **không** có thư mục gốc `mimic_<ver>/`, **không** có `VERSION` (bình thường). Phải `mkdir` thư mục `mimic_<ver>` trước rồi `tar -C` vào đó. `mimic_<ver>-darwin-arm64` đã kiểm thử với app trên macOS arm64 (2026-10-11); `darwin-amd64` / `linux-amd64` / `windows-amd64` chưa chạy thử |
| Repack macOS arm64 (dự phòng) | `mimic_<ver>-darwin.tar.gz` | nén lại từ `~/mlx/deps/mimic_<ver>/` | chỉ 4 phiên bản; có sẵn thư mục gốc `mimic_<ver>/` nên giải nén một lệnh `tar -C ~/mlx/deps`; cùng bytes với gói gốc, thêm `VERSION` và vài file 0-byte vô hại |

## Mimic

| Phiên bản | darwin-arm64 | darwin-amd64 | linux-amd64 | windows-amd64 | repack `-darwin` |
|---|---|---|---|---|---|
| 154.2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 153.2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 152.6 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 151.1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 150.4 | ✓ | ✓ | ✓ | ✓ | – |
| 149.2 | ✓ | ✓ | ✓ | ✓ | – |

## Stealthfox (chỉ lưu trữ — MintMultiX chưa chạy được core này)

| Phiên bản | darwin-arm64 | darwin-amd64 | linux-amd64 | windows-amd64 |
|---|---|---|---|---|
| 146.7 | ✓ | ✓ | ✓ | ✓ |
| 146.5 | ✓ | ✓ | ✓ | ✓ |
| 145.3 | ✓ | ✓ | ✓ | ✓ |
| 145.1 | ✓ | ✓ | ✓ | ✓ |
| 144.1 | ✓ | ✓ | ✓ | ✓ |
| 143.2 | ✓ | ✓ | ✓ | ✓ |
| 142.3 | ✓ | ✓ | ✓ | ✓ |
| 142.2 | ✓ | ✓ | ✓ | ✓ |
| 141.4 | ✓ | ✓ | ✓ | ✓ |

## Khôi phục core Mimic vào kho của app (macOS arm64)

Mặc định — gói gốc (phải tạo thư mục `mimic_<ver>` trước):

```sh
mkdir -p ~/mlx/deps/mimic_154.2 && tar -xzf mimic_154.2-darwin-arm64.tar.gz -C ~/mlx/deps/mimic_154.2
ls ~/mlx/deps/mimic_154.2        # Chromium.app  adapter.bin
```

Dự phòng — bản repack (đã có sẵn thư mục gốc, không `mkdir`):

```sh
tar -xzf mimic_154.2-darwin.tar.gz -C ~/mlx/deps
```

Máy Intel: cùng cách với `-darwin-amd64` (chưa chạy thử). Giải nén gói gốc thẳng vào `~/mlx/deps` sẽ làm file văng ra ngoài thư mục phiên bản — luôn tạo `mimic_<ver>` trước.

Hướng dẫn chi tiết (kể cả cách dùng `mimicsetup -adopt`): [`docs/user/restore-core-macos.md`](https://github.com/OmniMintX/MintMultiX/blob/main/docs/user/restore-core-macos.md) trong repo MintMultiX.
