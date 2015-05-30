# Đẩy ứng dụng của bạn lên Github

*Viết bởi Alyson La, [@realalysonla](https://www.twitter.com/realalysonla)*

## Các thứ cần chuẩn bị trước khi bắt đầu

### Git & GitHub

- Kiểm tra nếu Git đã được cài đặt
  - Trong terminal nhập `git --version` (khuyến khích dùng phiên bản 1.8 hoặc mới hơn)
- Nếu chưa có, tải Git [ở đây](http://git-scm.com/downloads). Sau đó, cài đặt hồ sơ Git cục bộ - trong terminal:
  - Nhập `git config --global user.name "tên-của-bạn"`
  - Nhập `git config --global user.email "email-của-bạn"`
  - To check if Git is already config-ed you can type git config --list
- Tạo tài khoản miễn phí trên [GitHub](https://github.com/) hoặc đăng nhập nếu bạn đã có tài khoản

**Huấn luyện viên**: Nói một chút về git, quản lý phiên bản và mã nguồn mở.

Talk a little about git, verison control, and open source

Push your app to GitHub using the command line

On your GitHub profile click “new repo” screen shot 2013-06-01 at 12 38 50 pm give it a name (example: rails-girls), brief description, choose the “public” repo option, and click “create repository”.

In the command line–make sure you cd into your railgirls folder–and type:

git init

This initializes a git repository in your project

Note: If you’ve already done the Heroku guide, then you’ve already initialized a git repository & you can move on to the next steps.

Next check if a file called READEME.rdoc exists in your railsgirl directory:

ls README.rdoc
Choose your operating system: Windows | Other
If the file doesn’t exist, create it by typing:

touch README.rdoc

COACH: Talk a little about README.rdoc

Then type:

git status

This will list out all the files in your working directory.

COACH: Talk about some of your favorite git commands

Then type:

git add .

This adds in all of your files & changes so far to a staging area.

Then type:

git commit -m "first commit"

This commits all of your files, adding the message “first commit”

Next type:

git remote add origin https://github.com/username/rails-girls.git

Your GitHub Repository page will list the repository URL, so feel free to copy and paste from there, rather than typing it in manually. You can copy and paste the link from your GitHub repository page by clicking the clipboard icon next to the URL.

This creates a remote, or connection, named “origin” pointing at the GitHub repository you just created.

Then type:

git push -u origin master

This sends your commits in your “master” branch to GitHub

Congratulations your app is on GitHub! Go check it out by going to the same url you used above: https://github.com/username/rails-girls (without the .git part)

If you want to continue making changes and pushing them to GitHub you’ll just need to use the following three commands:

git add .

git commit -m "type your commit message here"

git push origin master

What’s next?

Be a Part of the Open Source Community

Follow your fellow Rails Girls & coaches on GitHub
Star or watch their projects
Fork a repo, then clone and push changes to your fork. Share the changes with the originator by sending them a pull request!
Create an issue on a project when you find a bug
Explore other open source projects - search by programming languange or key word
Learn more Git

Check out trygit.org
Use a Git Cheatsheet
Look up Git Commands at git-scm.org
This work is licensed under a Creative Commons Attribution-Share Alike 3.0 License

Rails Girls · Crafted with excitement from Helsinki, Finland · Follow us on Twitter and Facebook