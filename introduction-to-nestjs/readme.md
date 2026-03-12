# Tổng qua về Nestjs

## 1. Lợi ích của Nestjs

### Cấu trúc chuẩn (Modular architecture)

- Mọi dev follow cùng 1 structure
- Dễ tìm code
- Dễ mở rộng
- Dễ maintain lâu dài

### Dependency Injection built-in

- Quản lý service, module rõ ràng
- Code sạch và testable

### Giảm boilerplate

- Dev chỉ tập trung business logic
- Không phải lo setup kiến trúc từ đầu

### Tăng scalability cho team

- Khi team lớn → vẫn giữ được consistency
- Dễ debug và thêm feature

## 2. Setup Nest.js

### Install Nesjt/cli Global

- pnpm install -g @nestjs/cli

### Create new project

- nest new project-name

## 3. Module

- Mỗi chức năng sẽ co 1 module riêng biệt
- Module này dùng module khác : Module import
- File module.ts sẽ kết nối các file khác lại với nhau
- AppModule la module duy nhất được import vào main.ts
- File module.ts là root file cho module
- 1 module sẽ có 3 phần: `Module: user.module.ts`
  `Controler: user.controller.ts`
  `Service: user.service.ts`

#### TIPS : Cách tạo 1 module bằng CLI

- `nest g module users ( create module )`
- `nest g controller users ( create controller )`
- `nest g service users ( create service )`
- `nest g res users ( create complete module )`

#### TIPS : Quy ước đặt tên

- Các file như `app.module.ts` , `app.controller.ts` chỉ là để
  lập trình viên nhận biết
- Chính các `Decorator` mới là thứ quyết định

#### TIPS : Cấu trúc thư mục

- tạo thư mục app/ trong trong src/ và di chuyển tất cả
  các file liên quan ( `module` | `controller` | `service` ) vào trong để đóng gói tốt hơn ( `tác giả khuyến khích đặt ở /src `)

#### TIPS : Nhiệm vụ của từng file

- `app.controler` chỉ lo việc điều hướng
- `app.module` kết nối controller và service lại với nhau
- `app.service` chứa logic nghiệp vụ

#### TIPS : Using module

- Các module con ( children module ) phải được import vao app module để tạo thành `cây module` để sử dụng

## 4. REST API ( Representational State Stranfer )

#### 1. Nugyên tắc thiết kế REST

- `Client Server Decoupling` ( `Tách biệt` ): Code phía client và server hoàn toàn độc lập , server cung cấp enpoint và client chỉ gọi và nhận kết quả
- `Stateless` ( `Không lưu trạng thái` ) : Server không lưu bất kỳ session nào của người dùng, mỗi request phải chứa đầy đủ thông tin để server hiểu ( `thường dùng Bear Token` trong Header)
- `Cacheability` ( `Khả năng lưu nháp` ): Dữ liệu có thể được lưu ở bộ nhớ đệm (Cache) `ở cả phía Client và Server để tăng tốc độ.`
- `Uniform Interface` ( `Giao diện thống nhất` ): Các API Endpoint phải có cấu trúc chung, dễ hiểu và phản hồi dữ liệu giống nhau cho `cùng một tài nguyên.`

- `Layered System` ( `Hệ thống phân lớp` ): Client không cần biết mình đang kết nối trực tiếp với Server hay qua các lớp trung gian (như Redis Cache, Database, Middleware).

#### 2. Các phương thức HTTP ( HTTP Verbs )

- GET: `Lấy dữ liệu` (Ví dụ: Xem danh sách bài viết).

- POST: `Tạo mới tài nguyên` (Ví dụ: Tạo một ghi chú mới).

- DELETE: `Xóa tài nguyên`.

- PUT: `Thay thế toàn bộ nội dung của một tài nguyên`.

- PATCH: `Cập nhật một phần nội dung` (Ví dụ: Chỉ đổi tiêu đề ghi chú).

#### 3. Các tool để test API

- `httpYac`
- `postman`

## 5. Controller

#### 1. Controller là cái gì ?????

- Đóng vai trò là người điều phối
- Nhiệm vụ là nhận các ` yêu cầu http từ client`
- Sử dụng `Decorator @Controller` để biến class bình thường thành controller
- `Controller cần được khai báo vào module` để có thể sử dụng

- Lệnh tạo controller `nest g co users | nest generate controller userss`

#### 2. Những Decorators cần nhớ

- `@Param()`
- `@Headers()`
- `@Query()`
- `@Ip()`
- `@Body()`

#### 3. Định nghĩa param trong controller

```
@Get(':id')
@Get(':id/{optional}')
```
