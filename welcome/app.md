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

Truy cập vào địa chỉ http://localhost:3000 từ trình duyệt. Nếu bạn sử dụng dịch-vụ đám-mây (như nitrous), hãy sử dụng tính năng xem trước (xem chi tiết ở [hướng dẫn cài đặt](install.md#using-a-cloud-service)).

Bạn sẽ thấy trang "Welcome aboard", thể hiện rằng việc khởi tạo ứng dụng hoạt động đúng như mong muốn.

Để ý thấy trên cửa sổ terminal không còn nhìn thấy command prompt vì bạn đang chạy Rails server, command prompt bây giờ trông như sau:

(trên Windows)

```shell
>
```

(trên Unix)

```shell
$
```

Khi command prompt không hiển thị, bạn không thể thực hiện các lệnh mới. Nếu bạn thử chạy `cd` hay một lệnh khác, nó sẽ không chạy. Để đưa command prompt về trạng thái bình thường:

Nhấn `CTRL-C` trong terminal để tắt server.

**Huấn luyện viên**: Giải thích ý nghĩa của mỗi lệnh. Những gì được tạo ra? Server làm những gì?

## 2. Create Idea scaffold

We’re going to use Rails’ scaffold functionality to generate a starting point that allows us to list, add, remove, edit, and view things; in our case ideas.

Coach: What is Rails scaffolding? (Explain the command, the model name and related database table, naming conventions, attributes and types, etc.) What are migrations and why do you need them?

```shell
rails generate scaffold idea name:string description:text picture:string
```

The scaffold creates new files in your project directory, but to get it to work properly we need to run a couple of other commands to update our database and restart the server.

```shell
bin/rake db:migrate
rails server
```

Choose your operating system: Windows | Other
Open http://localhost:3000/ideas in your browser. Cloud service (e.g. nitrous) users need to append ‘/ideas’ to their preview url instead (see installation guide).

Click around and test what you got by running these few command-line commands.

Hit CTRL-C to quit the server again when you’ve clicked around a little.

## 3. Thiết kế

Coach: Talk about the relationship between HTML and Rails. What part of views is HTML and what is Embedded Ruby (ERB)? What is MVC and how does this relate to it? (Models and controllers are responsible for generating the HTML views.)

The app doesn’t look very nice yet. Let’s do something about that. We’ll use the Twitter Bootstrap project to give us nicer styling really easily.

Mở `app/views/layouts/application.html.erb` bằng trình soạn thảo và trên dòng

```html
<%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track" => true %>
```

thêm

```html
<link rel="stylesheet" href="//railsgirls.com/assets/bootstrap.css">
<link rel="stylesheet" href="//railsgirls.com/assets/bootstrap-theme.css">
```

và thay

```html
<%= yield %>
```

bằng

```html
<div class="container">
  <%= yield %>
</div>
```

Cùng thêm một thanh điều hướng và 'footer' vào bố cục nữa nhé. Trong cùng tập tin đang mở, thêm vào dưới `<body>` 

```html
<nav class="navbar navbar-default navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="/">The Idea app</a>
    </div>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <li class="active"><a href="/ideas">Ideas</a></li>
      </ul>
    </div>
  </div>
</nav>
```

và trước `</body>`, thêm

```html
<footer>
  <div class="container">
    Rails Girls 2015
  </div>
</footer>
<script src="//railsgirls.com/assets/bootstrap.js"></script>
```

Now let’s also change the styling of the ideas table. Mở `app/assets/stylesheets/application.css` và thêm vào phía dưới cùng:

```css
body { padding-top: 100px; }
footer { margin-top: 100px; }
table, td, th { vertical-align: middle; border: none; }
th { border-bottom: 1px solid #DDD; }
```

Now make sure you saved your files and refresh the browser to see what was changed. You can also change the HTML & CSS further.

In case your Terminal shows you an error message that sort of implies there is something wrong with your JavaScript or CoffeeScript, install nodejs. This issue should not appear when you’ve used the RailsInstaller (but when you’ve installed Rails via gem install rails).

**Huấn luyện viên**: Nói một chút về CSS và bố cục trang web.

## 4. Thêm chức năng tải ảnh lên

Chúng ta cần cài đặt thêm 1 phần mềm để có thể tải lên tập tin trong Rails.

Mở Gemfile trong thư mục của dự án bằng trình soạn thảo và dưới dòng

```ruby
gem 'sqlite3'
```

thêm

```ruby
gem 'carrierwave'
```

Coach: Explain what libraries are and why they are useful. Describe what open source software is.

Hit CTRL-C in the terminal to quit the server.

In the terminal run:

```shell
bundle
```

Now we can generate the code for handling uploads. In the terminal run:

```shell
rails generate uploader Picture
```

Please start the rails server now.

Note: Some people might be using a second terminal to run the rails server continuously. If so you need to restart the Rails server process now. This is needed for the app to load the added library.

Mở `app/models/idea.rb` và dưới dòng

```ruby
class Idea < ActiveRecord::Base
```

thêm

```ruby
mount_uploader :picture, PictureUploader
```

Mở `app/views/ideas/_form.html.erb` và đổi

```html
<%= f.text_field :picture %>
```

thành

```html
<%= f.file_field :picture %>
```

Sometimes, you might get an TypeError: can’t cast ActionDispatch::Http::UploadedFile to string.

If this happens, in file app/views/ideas/_form.html.erb change the line

```html
<%= form_for(@idea) do |f| %>
```

thành

```html
<%= form_for @idea, :html => {:multipart => true} do |f| %>
```

In your browser, add new idea with a picture. When you upload a picture it doesn’t look nice because it only shows a path to the file, so let’s fix that.

Mở `app/views/ideas/show.html.erb` và đổi

```html
<%= @idea.picture %>
```

thành

```html
<%= image_tag(@idea.picture_url, :width => 600) if @idea.picture.present? %>
```

Now refresh your browser to see what changed.

**Huấn luyện viên**: Nói một chút về HTML.

## 5. Finetune the routes

Open http://localhost:3000 (or your preview url, if you are using a cloud service). It still shows the “Welcome aboard” page. Let’s make it redirect to the ideas page.

Mở `config/routes.rb` và thêm vào sau dòng đầu tiên

```ruby
root :to => redirect('/ideas')
```

Test the change by opening the root path (that is, http://localhost:3000/ or your preview url) in your browser.

Coach: Talk about routes, and include details on the order of routes and their relation to static files.

Rails 3 users: You will need to delete the index.html from the /public/ folder for this to work.

## Tạo trang tĩnh cho ứng dụng

Lets add a static page to our app that will hold information about the author of this application — you!

```shell
rails generate controller pages info
```

This command will create you a new folder under app/views called /pages and under that a file called info.html.erb which will be your info page.

It also adds a new simple route to your routes.rb.

```ruby
get "pages/info"
```

Now you can open the file app/views/pages/info.html.erb and add information about you in HTML. To see your new info page, take your browser to http://localhost:3000/pages/info or, if you are a cloud service user, append ‘/pages/info’ to your preview url.

## 6+. What next?

- Add design using HTML & CSS
- Add ratings
- Use CoffeeScript (or JavaScript) to add interaction
- Add picture resizing to make loading the pictures faster

## Additional Guides

Guide 0: Handy cheatsheet for Ruby, Rails, console etc.
Guide 1: Add commenting by Janika Liiv
Guide 2: Put your app online with Heroku by Terence Lee / Put your app online with OpenShift by Katie Miller / Put your app online with Shelly Cloud / Put your app online with anynines / Put your app online with Trucker.io
Guide 3: Create thumbnail images for the uploads by Miha Filej
Guide 4: Add design using HTML & CSS by Alex Liao
Guide 5: Add Authentication (user accounts) with Devise by Piotr Steininger
Guide 6: Adding profile pictures with Gravatar
Guide 7: Test your app with RSpec
Guide 8: Continuous Deployment with Travis-CI / Continuous Deployment with Codeship
Guide 9: Go through additional explanations for the App by Lucy Bain

