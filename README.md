# Watch Shop (Laravel)

Website bán đồng hồ xây dựng bằng Laravel với kiến trúc MVC, sử dụng migrations, seeders và xác thực người dùng với Breeze, giữ giao diện hiện đại và đầy đủ tính năng thương mại điện tử.

## 1) Mục tiêu sản phẩm
- Website bán đồng hồ: duyệt sản phẩm, lọc theo danh mục, chi tiết sản phẩm.
- Giỏ hàng, danh sách yêu thích, đặt hàng (checkout), lịch sử đơn hàng.
- Trang liên hệ, giới thiệu, và chatbot giao diện.
- Khu vực quản trị (dashboard, quản lý sản phẩm/đơn hàng) – có phân quyền admin.

## 2) Kiến trúc & cấu trúc thư mục chính
```
watch-shop-laravel/
├── app/
│   ├── Http/
│   │   ├── Controllers/            
│   │   └── Middleware/             
│   ├── Models/                     
│   └── ...
├── bootstrap/
├── config/
├── database/
│   ├── migrations/                 # Migrations: users, products, cart, wishlist, orders, messages
│   └── seeders/                    # UserSeeder, ProductSeeder, DatabaseSeeder
├── public/
│   ├── css/                        
│   ├── js/                        
│   ├── images/                     
│   └── flowers/                  
├── resources/
│   └── views/                     
│       ├── layouts/                
│       ├── home.blade.php
│       ├── shop.blade.php
│       ├── cart.blade.php
│       ├── wishlist.blade.php
│       ├── checkout.blade.php
│       ├── orders.blade.php
│       ├── view_page.blade.php
│       ├── about.blade.php
│       └── contact.blade.php
├── routes/
│   └── web.php                     
├── .env.example
         
```

## 3) CSDL & migrations
- Bảng `users`: name, email, password, user_type (admin/user), sdt, diachi, ...
- Bảng `products`: name, details, price, image, category
- Bảng `cart`: user_id, pid (product_id), name, price, quantity, image
- Bảng `wishlist`: user_id, pid, name, price, image
- Bảng `orders`: user_id, name, number, email, method, address, total_products, total_price, placed_on, payment_status
- Bảng `messages`: user_id, name, email, number, message

Tất cả được tạo bằng Laravel Migrations. Dữ liệu mẫu (25 sản phẩm, tài khoản người dùng) được đưa vào bằng Seeders.

## 4) Luồng nghiệp vụ chính
- Trang chủ (Home): hiển thị sản phẩm nổi bật.
- Cửa hàng (Shop): liệt kê, lọc theo danh mục, xem chi tiết sản phẩm.
- Yêu thích (Wishlist): thêm/xóa sản phẩm yêu thích.
- Giỏ hàng (Cart): thêm/cập nhật/xóa, tính tổng tiền.
- Thanh toán (Checkout): validate thông tin, tạo đơn hàng, xoá giỏ hàng sau đặt.
- Đơn hàng (Orders): xem lịch sử đặt hàng của người dùng.
- Liên hệ (Contact): gửi phản hồi (lưu vào `messages`).
- Quản trị (Admin): phân quyền qua `AdminMiddleware` (định nghĩa route nhóm `admin`).

## 5) Công cụ & công nghệ sử dụng
- Backend: **Laravel** (PHP 8.2), **Eloquent ORM**, **Blade**.
- Xác thực: **Laravel Breeze** (đăng ký/đăng nhập, bảo vệ CSRF, session, validations).
- Database: **MySQL/MariaDB** (có thể dùng MySQL từ XAMPP, MySQL độc lập hoặc Docker – Laravel Sail).
- Frontend: **Bootstrap 5.3**, **Font Awesome 6**, **CSS/JS** (kế thừa từ dự án gốc), **Vite** (bundling khi cần).
- Thư viện phụ trợ (admin/stats có thể dùng): **Chart.js**, **xlsx (SheetJS)**.
- Quản lý gói: **Composer** (PHP), **npm** (JS).

## 6) Điểm nổi bật
- Áp dụng chuẩn **MVC** rõ ràng, tách biệt Controller/Model/View.
- **Migrations** giúp quản lý phiên bản CSDL, dễ `migrate/rollback`.
- **Seeders** tạo dữ liệu mẫu tức thì, đồng nhất giữa các môi trường.
- **Middleware** phân quyền admin an toàn, dễ mở rộng.
- **Blade** giúp tái sử dụng layout, giữ nguyên giao diện dự án gốc.

## 7) Yêu cầu hệ thống (tóm tắt)
- PHP ≥ 8.1, Composer, MySQL/MariaDB, Node.js & npm.

## 8) Lệnh nhanh (tham khảo)
```bash
# Cài đặt
composer install
npm install  # nếu cần build assets

# Cấu hình
copy .env.example .env
php artisan key:generate
# Cập nhật DB_* trong .env cho MySQL bạn dùng

# Database
php artisan migrate --seed

# Chạy server
php artisan serve  # http://localhost:8000

# (Tuỳ chọn) Build assets
npm run dev   # hoặc npm run build
```
