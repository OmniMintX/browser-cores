# browser-cores

Kho lưu trữ browser core do Multilogin phát hành: **Mimic** (Chromium) và **Stealthfox** (Firefox). Các gói là tarball gốc tải từ CDN Multilogin, không chỉnh sửa, không ký code. Toàn bộ gói nằm trong release cuốn chiếu [`browser-cores`](https://github.com/OmniMintX/browser-cores/releases/tag/browser-cores); repo chỉ chứa `README.md` và `SHA256SUMS`.

## Tải và kiểm tra checksum

```sh
BASE=https://github.com/OmniMintX/browser-cores/releases/download/browser-cores
curl -LO $BASE/mimic_154.2-darwin-arm64.tar.gz
curl -LO $BASE/SHA256SUMS
shasum -a 256 -c --ignore-missing SHA256SUMS
```

Cách khác với GitHub CLI:

```sh
gh release download browser-cores --repo OmniMintX/browser-cores \
  --pattern 'mimic_154.2-darwin-arm64.tar.gz' --pattern SHA256SUMS
```

Tên asset: `<browser>_<ver>-<os>-<arch>.tar.gz`. `SHA256SUMS` trên nhánh `main` và trên release là cùng một file (64 dòng).

## Mimic

| Phiên bản | darwin-arm64 | darwin-amd64 | linux-amd64 | windows-amd64 | repack `-darwin` |
|---|---|---|---|---|---|
| 154.2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 153.2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 152.6 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 151.1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 150.4 | ✓ | ✓ | ✓ | ✓ | – |
| 149.2 | ✓ | ✓ | ✓ | ✓ | – |

Gói repack `mimic_<ver>-darwin.tar.gz` (chỉ macOS arm64, 4 phiên bản) có sẵn thư mục gốc `mimic_<ver>/` và file `VERSION`; gói gốc `-darwin-arm64` cùng nội dung nhưng file nằm ngay ở gốc archive, không có `VERSION`.

## Stealthfox

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
