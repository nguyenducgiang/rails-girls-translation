# Hướng dẫn làm ứng dụng Rails Girls

*Viết bởi Vesa Vänskä, [@vesan](https://twitter.com/vesan)*

**Hãy chắc chắn rằng bạn đã cài đặt Rails. [Làm theo hướng dẫn cài đặt](install.md)** để bắt đầu.

## Làm quen với các công cụ

### Trình soạn thảo

- Atom, Sublime Text, Vim và Emacs là một số trình soạn thảo bạn có thể sử dụng cho việc viết mã và chỉnh sửa tập tin.

### Terminal (hay Command Prompt trên Windows)

- Nơi bạn khởi động rails server hay chạy lệnh.

### Trình duyệt

- (Firefox, Safari, Chrome) để xem ứng dụng của bạn.

### Chú ý

Bạn cần chú ý lựa chọn chỉ dẫn chính xác cho hệ điều hành của mình - các lệnh cần chạy trên Windows sẽ khác một chút so với Mac và Linux. Lưu ý những chỗ có chú thích riêng cho Windows. Nếu bạn dùng một dịch-vụ đám-mây (như nitrous), bạn cần chạy các lệnh cho Linux ngay cả khi bạn đang dùng máy tính chạy trên Windows.

## 1. Khởi tạo ứng dụng

Chúng ta sẽ khởi tạo một ứng dụng Rails mới với tên gọi *railsgirls*.

Trước hết, hãy mở terminal lên:

- Mac OS X: Mở Spotlight, nhập *Terminal* và nhấn vào ứng dụng *Terminal*.
- Windows: Nhấn Start và tìm *Command Prompt*, rồi nhấn vào *Command Prompt with Ruby on Rails*.
- Linux (Ubuntu/Fedora): Tìm *Terminal* trên bảng điều khiển và nhấn *Terminal*.
- Dịch-vụ đám-mây (như nitrous): Đăng nhập vào tài khoản, khởi động box của bạn và chuyển sang IDE (xem chi tiết ở [hướng dẫn cài đặt](install.md#using-a-cloud-service)). Terminal thường nằm phía dưới cùng của cửa sổ trình duyệt.

Tiếp theo nhập các lệnh sau vào terminal:

```shell
mkdir projects
```

Bạn có thể xác nhận thư mục `projects` đã được tạo bằng cách chạy lệnh `ls` (`dir` cho Windows). Bạn có thể nhìn thấy tên thư mục `projects` hiện ra trên màn hình. Tiếp theo, bạn sẽ muốn chuyển thư mục hiện tại tới thư mục `projects` bằng lệnh:

```shell
cd projects
```

Bạn có thể xác nhận đang ở trong một thư mục rỗng bằng cách chạy lại lệnh `ls` (`dir` cho Windows). Bây giờ chúng ta sẽ khởi tạo một ứng dụng với tên là `railsgirls` với lệnh:

```shell
rails new railsgirls
```

Lệnh này sẽ tạo ra một ứng dụng mới trong thư mục `railsgirls`, vì thế chúng ta sẽ chuyển thư mục hiện tại tới ứng dụng Rails này bằng lệnh:

```shell
cd railsgirls
```

Nếu bạn chạy lệnh `ls` (`dir` cho Windows) ở đây, bạn sẽ thấy các thư mục như `app` hay `config`. Bạn có thể khởi động rails server ngay bây giờ với lệnh:

```shell
rails server
```




