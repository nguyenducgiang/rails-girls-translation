---
layout: default
title: Thêm tính năng bình luận cho ứng dụng Rails Girls
permalink: commenting
---

# Thêm tính năng bình luận cho ứng dụng Rails Girls

*Viết bởi Janika Liiv, [@janikaliiv](https://twitter.com/janikaliiv)*

Chúng ta sẽ bổ sung thêm khả năng thêm bình luận (comment) vào ý tưởng (idea) cho ứng dụng *railsgirls*.

Hướng dẫn cài đặt Rails và xây dựng ứng dụng ý-tưởng (idea) có thể xem [tại đây](/app).

## *1.* Tạo scaffold cho bình luận (comment)

Tạo một scaffold cho bình luận (comment), với tên người bình luận, nội dung của bình luận và tham chiếu tới bảng ý-tưởng (ideas) (`idea_id`)

```sh
rails g scaffold comment user_name:string body:text idea_id:integer
```

Lệnh này sẽ tạo ra một tệp tin migration có tác dụng thông báo cho cơ sở dữ liệu (database) về bảng comments mới. Chạy các tệp tin migrations với

```sh
rake db:migrate
```

## *2.* Thêm quan hệ vào các models

Bạn cần đảm bảo rằng Rails biết về mối quan hệ giữa các đối tượng (ở đây là **ideas** và **comments**). Vì một ý-tưởng (idea) có thể có nhiều bình-luận (comments) nên chúng ta cần đảm bảo model Idea biết điều này.

Mở `app/models/idea.rb` và dưới dòng

```ruby
class Idea < ActiveRecord::Base
```

thêm

```ruby
has_many :comments
```

The comment also has to know that it belongs to an idea. So open `app/models/comment.rb` and after

Bình-luận (comment) cũng cần phải biết rằng nó thuộc về một ý-tưởng (idea). Nên hãy mở `app/models/comment.rb` và sau dòng

```ruby
class Comment < ActiveRecord::Base
```

thêm

```ruby
belongs_to :idea
```

## *3.* Hiển thị biểu mẫu thêm bình-luận (comment form) và các bình luận đã có

Mở `app/views/ideas/show.html.erb` và sau `image_tag`

```erb
<%= image_tag(@idea.picture_url, :width => 600) if @idea.picture.present? %>
```

thêm

```erb
<h3>Comments</h3>
<% @comments.each do |comment| %>
  <div>
    <strong><%= comment.user_name %></strong>
    <br />
    <p><%= comment.body %></p>
    <p><%= link_to 'Delete', comment_path(comment), method: :delete, data: { confirm: 'Are you sure?' } %></p>
  </div>
<% end %>
<%= render 'comments/form' %>
```

Trong `app/controllers/ideas_controller.rb` thêm vào action `show` sau dòng

```ruby
@idea = Idea.find(params[:id])
```

đoạn mã sau

```ruby
@comments = @idea.comments.all
@comment = @idea.comments.build
```

Mở `app/views/comments/_form.html.erb` và sau đoạn

```erb
  <div class="field">
    <%= f.label :body %><br />
    <%= f.text_area :body %>
  </div>
```

thêm dòng sau

```erb
<%= f.hidden_field :idea_id %>
```

sau đó, xóa

```erb
<div class="field">
  <%= f.label :idea_id %><br>
  <%= f.number_field :idea_id %>
</div>
```

Vậy là xong. Bây giờ bạn có thể xem ý-tưởng (idea) bạn đã thêm vào ứng dụng trước đây, ở đó bạn sẽ thấy các bình luận cũ và biểu mẫu để thêm bình-luận (comment) mới.
