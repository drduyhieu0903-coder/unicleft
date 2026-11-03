# Cleft lip repair simulator · Mô phỏng mổ khe hở môi một bên

Static, dependency-free web app (no build step). Unilateral cleft lip repair – modified Millard rotation–advancement + Hamdan sliding V + ABFSS – 70 sub-steps, 2D/3D, caliper, 11 symmetry criteria.
*For education only – schematic, not clinical measurements.*

| Path | Content |
|---|---|
| `/` | Language chooser (Netlify redirects by browser language) |
| `/en/` | **English only** (no Vietnamese text) |
| `/vi/` | **Tiếng Việt** only |
| `/bilingual/` | EN + VI with EN / EN+VI / VI toggle, mobile-first layout |
| `/vendor/` | three.js r128 + OrbitControls (MIT) – self-hosted, no CDN needed |
| `/tools/strip_book_images.py` | Removes the embedded book figures (see Copyright) |

## Run locally
```bash
python3 -m http.server 8080      # then open http://localhost:8080
```

## Deploy – GitHub → Netlify
1. `git init && git add . && git commit -m "Cleft lip simulator"`
2. Create an empty repo on GitHub, then `git remote add origin <url> && git branch -M main && git push -u origin main`
3. Netlify → **Add new site → Import from Git** → pick the repo.
   Build command: *(empty)* · Publish directory: `.` (settings are also in `netlify.toml`).
4. Quick alternative: drag the folder onto <https://app.netlify.com/drop>.
5. Optional: Site settings → Domain management → custom domain / HTTPS (automatic).

Security headers (CSP, HSTS, nosniff) and caching are defined in `netlify.toml`. The CSP allows only same-origin scripts plus inline code and `data:` images.

## Copyright – read before publishing
The step photos and line diagrams embedded in the three pages are reproduced from **Chapter 6, Abdul-Aziz & Hamdan, *Video Atlas of Cleft Lip and Palate Surgery*** (Rogers, Hartnick, Hamdan). They belong to their rights holders. Use them only with permission. For a public site without them run:
```bash
python3 tools/strip_book_images.py
```
three.js: © mrdoob and contributors, MIT license (`vendor/THREE-LICENSE.txt`).

## Tiếng Việt – triển khai nhanh
1. Đẩy thư mục này lên GitHub (lệnh ở trên).
2. Netlify → *Import from Git*; để trống Build command; Publish directory = `.`.
3. **Bản quyền:** ảnh/sơ đồ lấy từ sách (Chương 6, Video Atlas of Cleft Lip and Palate Surgery). Chỉ công khai khi được phép, hoặc chạy `python3 tools/strip_book_images.py` để bỏ ảnh.
4. Trang chỉ dùng để học tập, không phải số đo lâm sàng.
