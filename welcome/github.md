# Đẩy ứng dụng của bạn lên GitHub

*Viết bởi Alyson La, [@realalysonla](https://www.twitter.com/realalysonla)*

## Các thứ cần chuẩn bị trước khi bắt đầu

### Git & GitHub

- Kiểm tra nếu Git đã được cài đặt
  - Trong terminal nhập `git --version` (khuyến khích dùng phiên bản 1.8 hoặc mới hơn)
- Nếu chưa có, tải Git [ở đây](http://git-scm.com/downloads). Sau đó, cài đặt hồ sơ Git cục bộ - trong terminal:
  - Nhập `git config --global user.name "tên-của-bạn"`
  - Nhập `git config --global user.email "email-của-bạn"`
  - Để kiểm tra xem Git đã được cấu hình hay chưa, chạy lệnh `git config --list`
- Tạo tài khoản miễn phí trên [GitHub](https://github.com/) hoặc đăng nhập nếu bạn đã có tài khoản

**Huấn luyện viên**: Nói một chút về Git, quản lý phiên bản và mã nguồn mở.

## Đẩy ứng dụng của bạn lên Github sử dụng dòng lệnh

Trên trang GitHub của bạn, nhấn vào "new repo" ![screen shot 2013-06-01 at 12 38 50 pm](https://f.cloud.github.com/assets/2623954/595307/eb70c6cc-caf2-11e2-9d2d-60deb31ac049.png), đặt tên cho repo (ví dụ: rails-girls), mô tả ngắn gọn, để tùy chọn "public" và nhấn vào "create repository".

Trong terminal, hãy chắc chắn bạn đã `cd` vào thư mục `railsgirls` và nhập:

```shell
git init
```

Lệnh này sẽ khởi tạo một git repository trong dự án của bạn.

*Lưu ý*: Nếu bạn đã làm theo [hướng dẫn cho Heroky](heroku.md), thì git repository đã được khởi tạo rồi và bạn có thể bỏ qua bước trên.

Tiếp theo kiểm tra nếu tập tin `READEME.rdoc` tồn tại trong thư mục `railsgirls`:

```shell
ls README.rdoc
```

(trên Windows)

```shell
dir README.rdoc
```

Nếu tập tin không tồn tại, tạo mới bằng lệnh:

```shell
touch README.rdoc
```

**Huấn luyện viên**: Nói một chút về README.rdoc

Sau đó nhập:

```shell
git status
```

Lệnh này sẽ liệt kê tất cả các tập tin trong thư mục `railsgirls` của bạn.

**Huấn luyện viên**: Nói về một vài lệnh yêu thích trong Git.

Sau đó nhập:

```shell
git add .
```

Lệnh này sẽ thêm tất cả các tập tin và thay đổi từ đầu tới giờ vào khu vực 'staging'.

Rồi nhập:

```shell
git commit -m "first commit"
```

Lệnh này sẽ 'commit' (ghi nhận các thay đổi) tất cả các tập tin ở trong khu vực "staging" với thông điệp đính kèm là "first commit".

Tiếp theo nhập:

```shell
git remote add origin https://github.com/username/rails-girls.git
```

Your GitHub Repository page will list the repository URL, so feel free to copy and paste from there, rather than typing it in manually. You can copy and paste the link from your GitHub repository page by clicking the clipboard icon next to the URL.

This creates a remote, or connection, named “origin” pointing at the GitHub repository you just created.

Sau đó nhập:

```shell
git push -u origin master
```

Lệnh này sẽ gửi các 'commit' của bạn tới nhánh "master" trên GitHub.

Congratulations your app is on GitHub! Go check it out by going to the same url you used above: https://github.com/username/rails-girls (without the .git part)

If you want to continue making changes and pushing them to GitHub you’ll just need to use the following three commands:

```shell
git add .
git commit -m "type your commit message here"
git push origin master
```

## What’s next?

### Trở thành một phần của Cộng đồng Mã nguồn Mở

- Theo đuôi những người cùng tham gia Rails Girls với bạn và các huấn luyện viên trên GiHub
- 'Star' (đánh dấu sao) hoặc 'watch' (đánh dấu theo dõi) các dự án của họ
- ['Fork'](https://help.github.com/articles/fork-a-repo) một 'repo', sau đó 'clone' và đẩy các thay đổi vào bản 'fork' của bạn. Chia sẻ các thay đổi này với người sở hữu dự án bằng cách gửi họ một 'pull request'!
- Tạo một 'issue' trên một dự án khi bạn phát hiện ra bug
- Khám phá các dự án mã nguồn mở khác - tìm kiếm theo ngôn ngữ lập trình hay từ khóa

### Học thêm về Git

- Thử [trygit.org](http://try.github.io/)
- Sử dụng một [Git Cheatsheet](https://na1.salesforce.com/help/doc/en/salesforce_git_developer_cheatsheet.pdf)
- Tra cứu các lệnh của Git tại [git-scm.org](http://git-scm.com/)