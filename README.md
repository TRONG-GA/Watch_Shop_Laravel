# Watch_Shop_Laravel
# 🚀 HƯỚNG DẪN CHẠY DỰ ÁN LARAVEL WATCH SHOP

## 📋 YÊU CẦU HỆ THỐNG

- **PHP**: >= 8.1 (khuyến nghị 8.2+)
- **Composer**: Latest version
- **MySQL/MariaDB**: 5.7+ hoặc 8.0+
- **Node.js**: 18+ (cho Vite)
- **NPM**: 8+

## 🔧 CÀI ĐẶT VÀ CẤU HÌNH

### Bước 1: Kiểm tra môi trường

```bash
# Kiểm tra PHP
php --version

# Kiểm tra Composer
composer --version

# Kiểm tra Node.js
node --version

# Kiểm tra NPM
npm --version
```

### Bước 2: Cài đặt dependencies

```bash
# Cài đặt PHP packages
composer install

# Cài đặt Node.js packages
npm install
```

### Bước 3: Cấu hình môi trường

```bash
# Copy file cấu hình
copy .env.example .env

# Tạo application key
php artisan key:generate
```

### Bước 4: Cấu hình database

Mở file `.env` và cập nhật thông tin database:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=watch_shop_laravel
DB_USERNAME=root
DB_PASSWORD=
```

### Bước 5: Tạo database

```sql
-- Tạo database trong MySQL
CREATE DATABASE watch_shop_laravel CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Bước 6: Chạy migrations và seeders

```bash
# Chạy migrations để tạo bảng
php artisan migrate

# Chạy seeders để tạo dữ liệu mẫu
php artisan db:seed
```

### Bước 7: Tạo storage link

```bash
# Tạo symbolic link cho storage
php artisan storage:link
```

### Bước 8: Build assets (tùy chọn)

```bash
# Build CSS và JS với Vite
npm run build

# Hoặc chạy development server
npm run dev
```

## 🚀 CHẠY ỨNG DỤNG

### Cách 1: Sử dụng Laravel Development Server

```bash
# Chạy server development
php artisan serve

# Ứng dụng sẽ chạy tại: http://localhost:8000
```

### Cách 2: Sử dụng XAMPP

1. Copy thư mục `watch-shop-laravel` vào `htdocs`
2. Truy cập: `http://localhost/watch-shop-laravel/public`

## 👥 TÀI KHOẢN MẪU

### Admin Account
- **Email**: admin@gmail.com
- **Password**: 123456
- **Quyền**: Admin (có thể truy cập admin dashboard)

### User Account
- **Email**: user01@gmail.com
- **Password**: 123456
- **Quyền**: User thường

### Test Account
- **Email**: test@gmail.com
- **Password**: 123456
- **Quyền**: Admin

## 📱 TÍNH NĂNG CHÍNH

### Cho Người Dùng:
- ✅ **Trang chủ** với carousel và sản phẩm nổi bật
- ✅ **Cửa hàng** với 25 sản phẩm đồng hồ đa dạng
- ✅ **Bộ lọc sản phẩm** theo danh mục
- ✅ **Chi tiết sản phẩm** với hình ảnh và mô tả
- ✅ **Giỏ hàng** với quản lý đầy đủ (thêm, sửa, xóa)
- ✅ **Danh sách yêu thích** 
- ✅ **Thanh toán** với form validation
- ✅ **Lịch sử đơn hàng**
- ✅ **Liên hệ** và giới thiệu
- ✅ **Chatbot** hỗ trợ khách hàng
- ✅ **Đăng ký/Đăng nhập** với Breeze

### Cho Admin:
- ✅ **Admin Dashboard** (sẽ được phát triển)
- ✅ **Quản lý sản phẩm** (CRUD)
- ✅ **Quản lý đơn hàng**
- ✅ **Thống kê doanh thu**

## 🗂️ CẤU TRÚC DỰ ÁN

```
watch-shop-laravel/
├── app/
│   ├── Http/Controllers/     # Controllers
│   ├── Models/              # Models với relationships
│   └── Http/Middleware/     # Middleware (AdminMiddleware)
├── database/
│   ├── migrations/          # Database migrations
│   └── seeders/            # Data seeders
├── resources/
│   └── views/              # Blade templates
│       ├── layouts/        # Layout chính
│       ├── home.blade.php  # Trang chủ
│       ├── shop.blade.php  # Cửa hàng
│       ├── cart.blade.php  # Giỏ hàng
│       └── ...
├── public/
│   ├── css/               # CSS files
│   ├── js/                # JavaScript files
│   ├── images/            # Hình ảnh
│   └── flowers/           # Hình ảnh sản phẩm
└── routes/
    └── web.php            # Web routes
```

## 🎨 GIAO DIỆN

- **Responsive Design**: Tương thích mobile và desktop
- **Bootstrap 5.3**: Framework CSS hiện đại
- **Font Awesome 6.0**: Icon library
- **Custom CSS**: Styling từ dự án gốc
- **Animation Effects**: Logo LED và UI animations
- **Chatbot**: JavaScript chatbot thông minh

## 🛠️ TROUBLESHOOTING

### Lỗi thường gặp:

1. **"Could not open input file: artisan"**
   ```bash
   # Đảm bảo bạn đang ở thư mục dự án
   cd watch-shop-laravel
   php artisan serve
   ```

2. **Database connection error**
   ```bash
   # Kiểm tra cấu hình .env
   # Đảm bảo MySQL đang chạy
   # Kiểm tra database đã được tạo chưa
   ```

3. **Permission denied**
   ```bash
   # Cấp quyền cho storage
   chmod -R 775 storage
   chmod -R 775 bootstrap/cache
   ```

4. **Class not found**
   ```bash
   # Chạy lại autoload
   composer dump-autoload
   ```

## 📊 DỮ LIỆU MẪU

- **25 sản phẩm đồng hồ** đa dạng từ các thương hiệu nổi tiếng
- **4 tài khoản mẫu** (2 admin, 2 user)
- **16 danh mục sản phẩm** khác nhau
- **Dữ liệu đầy đủ** cho testing

## 🔐 BẢO MẬT

- **CSRF Protection**: Tự động với Laravel
- **Form Validation**: Validation rules đầy đủ
- **SQL Injection Protection**: Eloquent ORM
- **XSS Protection**: Blade templating
- **Authentication**: Laravel Breeze
- **Authorization**: Middleware phân quyền

## 📈 PERFORMANCE

- **Eloquent ORM**: Query optimization
- **Lazy Loading**: Relationships
- **Caching**: Laravel cache system
- **Asset Optimization**: Vite bundling
- **Database Indexing**: Foreign keys và indexes

## 🚀 DEPLOYMENT

### Production Checklist:
- [ ] Cấu hình `.env` cho production
- [ ] Set `APP_DEBUG=false`
- [ ] Cấu hình database production
- [ ] Chạy `php artisan config:cache`
- [ ] Chạy `php artisan route:cache`
- [ ] Chạy `php artisan view:cache`
- [ ] Build assets với `npm run build`
      
---

**🎉 Chúc bạn sử dụng dự án thành công!**

