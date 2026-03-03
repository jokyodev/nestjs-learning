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

## Setup Nest.js

### Install Nesjt/cli Global

- pnpm install -g @nestjs/cli

### Create new project

- nest new project-name

## 2. Module

- Mỗi chức năng sẽ co 1 module riêng biệt
- Module này dùng module khác : Module import
- 1 module sẽ có 3 phần: `Module: user.module.ts`
  `Controler: user.controller.ts`
  `Service: user.service.ts`
