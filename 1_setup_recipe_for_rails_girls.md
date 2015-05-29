# Công thức cài đặt cho Rails Girls

*Thời gian chế biến: 5 phút chủ động / 15 - 30 phút thụ động*

Để xây dựng ứng dụng và những thứ khác với Ruby on Rails, chúng ta cần cài đặt một số phần mềm và môi trường làm việc cho máy tính của bạn.

Hãy thực hiện theo các hướng dẫn cho hệ điều hành của bạn. Đừng sợ nếu bạn gặp phải bất cứ trở ngại nào. Hãy báo cho chúng tôi biết (tại sự kiện) để chúng ta có thể cùng nhau giải quyết.

- Cài đặt cho OS X
- Cài đặt cho Windows
- Cài đặt cho Linux
- Giái pháp cài đặt thay thế cho tất cả các OS
- Sử dụng một Dịch-vụ Đám-mây - Không cần cài đặt

## Cài đặt cho OS X

### 1. Kiểm tra phiên bản hệ điều hành.

Nhấn vào trình-đơn Apple và chọn *About this Mac*.

![Apple menu](http://guides.railsgirls.com/images/1.png)

### 2. Trong cửa sổ hiện ra bạn sẽ thấy phiên bản của hệ điều hành.

Nếu phiên bản của bạn bắt đầu với 10.6, 10.7, 10.8, 10.9 hoặc 10.10, hãy làm theo hướng dẫn này. Ngược lại, chúng tôi có thể cài đặt giúp bạn tại sự kiện.

![About this Mac dialog](http://guides.railsgirls.com/images/2.png)

### 3a. Nếu phiên bản OS X của bạn là 10.9 hoặc mới hơn:

Nếu phiên bản của bạn bắt đầu bằng 10.9 hoặc 10.10, hãy thực hiện theo các bước dưới đây. Chúng ta sẽ cài đặt homebrew và rbenv

#### 3a1. Cài đặt các công-cụ dòng-lệnh trên terminal:

```shell
xcode-select --install
```

#### 3a2. Cài đặt [Homebrew](http://brew.sh/):

```shell
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### 3a3. Cài đặt [rbenv](https://github.com/sstephenson/rbenv):

```shell
brew update
brew install rbenv rbenv-gem-rehash ruby-build
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
echo 'export PATH="$HOME/.rbenv/shims:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
```

#### 3a4. Build Ruby với rbenv:

Bạn có thể dùng lệnh “rbenv install -l” để xem phiên bản Ruby mới nhất.

```shell
rbenv install 2.2.0
```

Nếu bạn gặp lỗi “OpenSSL::SSL::SSLError: … : certificate verify failed”, hãy thử cách sau.

```shell
brew install curl-ca-bundle
cp /usr/local/opt/curl-ca-bundle/share/ca-bundle.crt `ruby -ropenssl -e 'puts OpenSSL::X509::DEFAULT_CERT_FILE'`
```

#### 3a5. Thiết lập phiên bản Ruby mặc định:

```shell
rbenv global 2.2.0
```

#### 3a6. Cài đặt Rails:

```shell
gem i rails --no-ri --no-rdoc
```

### 3b. Nếu phiên bản OS X của bạn là 10.6, 10.7, hoặc 10.8:

Tải RailsInstaller phù hợp với phiên bản OS X:

- [RailsInstaller for 10.7 and 10.8](http://railsinstaller.s3.amazonaws.com/RailsInstaller-1.0.4-osx-10.7.app.tgz) *(325MB)*
- [RailsInstaller for 10.6](http://railsinstaller.s3.amazonaws.com/RailsInstaller-1.0.4-osx-10.6.app.tgz) *(224MB)*

Nháy đúp vào tệp tin tải về, nó sẽ được giải nén vào cùng thư mục mà nó đang ở trong. Nháy đúp vào tệp tin vừa được giải nén 'RailsInstaller-1.0.4-osx-10.7.app' hoặc 'RailsInstaller-1.0.4-osx-10.6.app' và làm theo hướng dẫn. Nó sẽ mở tệp tin README với tiêu đề 'Rails Installer OS X'. Đừng quan tâm đến tệp tin này.

Nếu phiên bản của Rails không phải là mới nhất, bạn có thể cập nhật bằng câu lệnh sau trên terminal.

```shell
gem update rails --no-ri --no-rdoc
```

Chạy lệnh khởi tạo ứng dụng để chắc chắn mọi thứ hoạt động như mong muốn.

```shell
rails new railsgirls
```

### 4. Cài đặt một trình soạn thảo văn bản để soạn thảo các tệp mã

Đối với workshop chúng tôi khuyến nghị sử dụng trình soạn thảo Atom.

- [Tải và cài đặt Atom](https://atom.io/)

Nếu bạn sử dụng Mac OS X 10.7 hoặc cũ hơn, bạn có thể dùng trình soạn thảo khác như [Sublime Text 2](http://www.sublimetext.com/2).

### 5. Cập nhật trình duyệt

Mở trang [whatbrowser.org](http://whatbrowser.org/) và cập nhật trình duyệt của bạn lên phiên bản mới nhất nếu có.

Như vậy là bạn đã thiết lập xong môi trường để làm việc với Ruby on Rails. Xin chúc mừng!

---

## Cài đặt cho Windows

## 1. Cài đặt Rails

Download RailsInstaller and run it. Click through the installer using the default options.

Mở `Command Prompt with Ruby on Rails` và chạy các lệnh sau:

```shell
rails -v
```

Nếu phiên bản Rails nhỏ hơn 4, cập nhật nó bằng lệnh sau:

```shell
gem update rails --no-ri --no-rdoc
```

Chạy lệnh khởi tạo ứng dụng để chắc chắn mọi thứ hoạt động như mong muốn.

```shell
rails new railsgirls
cd railsgirls
rails server
```

## Các lỗi có thể xảy ra

### Lỗi Gem::RemoteFetcher

Nếu bạn gặp phải lỗi dưới đây khi chạy `rails new railsgirls` hay `gem update rails`:

```shell
Gem::RemoteFetcher::FetchError: SSL_connect returned=1 errno=0 state=SSLv3 read
server certificate B: certificate verify failed (https://rubygems.org/gems/i18n-
0.6.11.gem)
```

Điều này có nghĩa là bạn đang sử dụng phiên bản Rubygems quá cũ và cần được cập nhật thủ công. Đầu tiên hãy kiểm tra phiên bản Rubygems đang dùng.

```shell
gem -v
```

Nếu phiên bản nhỏ hơn 2.2.3, bạn cần cập nhật thủ công như sau:

Đầu tiên tải [ruby-gems-update gem](https://github.com/rubygems/rubygems/releases/download/v2.2.3/rubygems-update-2.2.3.gem) về. Di chuyển tệp tin tới `c:\\rubygems-update-2.2.3.gem` và chạy:

```shell
gem install --local c:\\rubygems-update-2.2.3.gem
update_rubygems --no-ri --no-rdoc
gem uninstall rubygems-update -x
```

Kiểm tra phiên bản của Rubygems

```shell
gem -v
```

Hãy chắc chắn là phiên bản lớn hơn 2.2.3. Chạy lại các lệnh bị lỗi lúc trước.

### Lỗi ‘x64_mingw’ is not a valid platform`

Đôi khi bạn gặp phải lỗi sau khi chạy `rails server`: `'x64_mingw' is not a valid platform`. Nếu gặp lỗi này sau khi cài RailsInstaller, bạn cần sửa đổi tệp tin `Gemfile` một chút:

Xem phần dưới cùng của tệp tin, có thể bạn sẽ thấy dòng cuối cùng như sau: `gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]`. Nếu dòng này có `:x64_mingw`, hãy xóa `:x64_mingw`. Sau khi sửa, dòng cuối cùng của tệp tin nên là: `'tzinfo-data', platforms: [:mingw, :mswin]`.

Sau khi hoàn thành việc sửa đổi, vui lòng dùng Command Prompt và chạy `bundle update`.

### 2. Cài đặt một trình soạn thảo văn bản để soạn thảo các tệp mã

Đối với workshop chúng tôi khuyến nghị sử dụng trình soạn thảo Atom.

- [Tải và cài đặt Atom](https://github.com/atom/atom/releases/latest)
  - Tải và giải nén tệp tin Atom cho Windows.
  - Sao chép thư mục (Atom) vào trong Program Files.
  - Chạy Atom từ thư mục.

Nếu bạn dùng Window Vista hoặc các phiên bản cũ hơn, bạn có thể dùng trình soạn thảo [Sublime Text 2](http://www.sublimetext.com/2)

Như vậy là bạn đã thiết lập xong môi trường để làm việc với Ruby on Rails. Xin chúc mừng!

### 3. Cập nhật trình duyệt

Nếu bạn đang dùng Internet Explorer, chúng tôi khuyến khích bạn cài đặt [Firefox](http://guides.railsgirls.com/install/mozilla.org/firefox) hay [Google Chrome](http://guides.railsgirls.com/install/google.com/chrome).

Mở trang [whatbrowser.org](http://whatbrowser.org/) và cập nhật trình duyệt của bạn lên phiên bản mới nhất nếu có.

---

## Cài đặt cho Linux

### 1. Cài đặt Rails

Để cài đặt môi trường phát triển cho Ruby on Rails bạn chỉ cần sao chép dòng lệnh dưới đây cho Linux (Ubunbu hoặc Fedora), dán vào Terminal và nhấn Enter. Sẽ mất một lúc để hoàn thành, trong thời gian đó hãy thưởng thức các con chữ bay nhảy trên màn hình. Chúng tôi khuyến khích các bạn kiếm chút đồ giải khát trước khi bắt đầu.

Trên Ubuntu:

```sh
bash < <(curl -sL https://raw.github.com/railsgirls/installation-scripts/master/rails-install-ubuntu.sh)
```

Nếu bạn định sử dụng RVM để cài đặt với gnome-terminal, có thể bạn sẽ cần thay đổi tùy chọn mặc định (của terminal) trước khi sử dụng được phiên bản Ruby on Rails phù hợp. Xem chi tiết: [RVM documentation](http://rvm.io/integration/gnome-terminal)

Trên Fedora:

```sh
bash < <(curl -sL https://raw.github.com/railsgirls/installation-scripts/master/rails-install-fedora.sh)
```

Chạy lệnh khởi tạo ứng dụng để chắc chắn mọi thứ hoạt động như mong muốn.

```sh
rails new railsgirls
cd railsgirls
rails server
```

### 2. Cài đặt một trình soạn thảo văn bản để soạn thảo các tệp mã

Đối với workshop chúng tôi khuyến nghị sử dụng trình soạn thảo Sublime Text.

- [Tải và cài đặt Sublime Text](http://www.sublimetext.com/2)

### 3. Cập nhật trình duyệt

Mở trang [whatbrowser.org](http://whatbrowser.org/) và cập nhật trình duyệt của bạn lên phiên bản mới nhất nếu có.

Như vậy là bạn đã thiết lập xong môi trường để làm việc với Ruby on Rails. Xin chúc mừng!

---

## Máy Ảo

Thay vì cài đặt các công cụ trên máy tính của bạn, bạn có thể thiết kế môi trường phát triển trên một máy ảo. Vui lòng xem chi tiết [tại đây](http://guides.railsgirls.com/virtual-machine).

---

## Sử dụng Dịch vụ Đám mây

Instead of installing Ruby on Rails and an editor on your computer, you can use a webservice for development. All you need is a browser and an internet connection. This guide explains how to get started with nitrous.io. If you’re using a different service, they may use a different wording - e.g. ‘workspace’ instead of ‘box’, but the process is usually pretty similar.

### 1. Cập nhật trình duyệt

Nếu bạn đang dùng Internet Explorer, chúng tôi khuyến khích bạn cài đặt [Firefox](http://guides.railsgirls.com/install/mozilla.org/firefox) hay [Google Chrome](http://guides.railsgirls.com/install/google.com/chrome).

Mở trang [whatbrowser.org](http://whatbrowser.org/) và cập nhật trình duyệt của bạn lên phiên bản mới nhất nếu có.

### 2. Tạo tài khoản miễn phí

Tới https://nitrous.io và đăng kí miễn phí.

### 3. Cài đặt một development box / workspace cho Ruby on Rails

- Đăng nhập vào tài khoản nitrous của bạn
- Go to the dashboard by using the green ‘Open dashboard’ button
- Create a nitrous box: pick Ruby/Rails from the templates - everything else can stay as is, but you can change the name of your box if you want to
- Sẽ mất một chút thời gian để development box sẵn sàng.

### 4. Find and restart your development box

- If you’ve just created your box, you can probably skip these steps - they’re good to know if you login to nitrous again later
- You can always find your nitrous boxes by going to the dashboard or choosing ‘Boxes’ from the top menu
- Pick your box from the list of boxes
- If you haven’t used a box in a while, it might have been shutdown due to inactivity. If you are informed that your box is not running, restart it using the respective button
- When your box is up and running, choose ‘IDE’ in order to start coding

### 5. Viết mã với development box

- Ở bên tay trái là cửa sổ duyệt tập tin, bạn có thể điều hướng giữa các tập tin và thư mục ở đây
- Ở giữa là trinh soạn thảo nơi bạn chỉnh sửa các tệp tin
- Ở phía dưới cùng, bạn sẽ thấy terminal để chạy lệnh
- Tất cả các thứ bạn cần có sẵn trên cửa sổ trình duyệt - bạn không cần mở thêm một trình soạn thảo hay terminal ở chỗ khác
- Nếu bạn đang làm theo các hướng dẫn, hãy sử dụng các lệnh cho Linux ngay cả khi bạn đang sử dụng một máy tính xài Windows
- Hệ điều hành bạn đang sử dụng không liên quan ở đây, vì tất cả các lệnh được chạy trên development box - một cỗ máy Linux
- Nếu một hướng dẫn đề nghị bạn trỏ trình duyệt tới một địa chỉ như `http://localhost:3000`, hãy vào trình đơn 'Preview' và chọn 'Port 3000'
- Nếu, tỉ dụ, bạn được đề nghị truy cập `http://localhost:3000/posts`, hãy thêm `/posts` thủ công vào URL đã được mở ở trên