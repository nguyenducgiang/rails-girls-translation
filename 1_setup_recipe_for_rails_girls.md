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

#### 3a3. Install rbenv:

brew update
brew install rbenv rbenv-gem-rehash ruby-build
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
echo 'export PATH="$HOME/.rbenv/shims:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
3a4. Build Ruby with rbenv:

You can find the newest version of Ruby with the command “rbenv install -l”.

rbenv install 2.2.0
If you got “OpenSSL::SSL::SSLError: … : certificate verify failed” error, try it this way.

brew install curl-ca-bundle
cp /usr/local/opt/curl-ca-bundle/share/ca-bundle.crt `ruby -ropenssl -e 'puts OpenSSL::X509::DEFAULT_CERT_FILE'`

3a5. Set default Ruby:

rbenv global 2.2.0

3a6. Install rails:

gem i rails --no-ri --no-rdoc
3b. If your OS X version is 10.6, 10.7, or 10.8:

Download the RailsInstaller for your version of OS X:

RailsInstaller for 10.7 and 10.8 (325MB)
RailsInstaller for 10.6 (224MB)
Double click the downloaded file and it will unpack it into the current directory. Double click the the newly unpacked ‘RailsInstaller-1.0.4-osx-10.7.app’ or ‘RailsInstaller-1.0.4-osx-10.6.app’ and follow the instructions. It will open a README file with ‘Rails Installer OS X’ at the top. Please ignore the instructions in this file.

If the Rails version wasn’t the latest, you could update it using a following command on terminal.

gem update rails --no-ri --no-rdoc
Make sure that all works well by running the application generator command.

rails new railsgirls
4. Install a text editor to edit code files

For the workshop we recommend the text editor Atom.

Download Atom and install it
If you are using Mac OS X 10.7 or older versions, you can use another editor Sublime Text 2.

5. Update your browser

Open whatbrowser.org and update your browser if you don’t have the latest version.

Now you should have a working Ruby on Rails programming setup. Congrats!

Setup for Windows

1. Install Rails

Download RailsInstaller and run it. Click through the installer using the default options.

Open Command Prompt with Ruby on Rails and run the following command:

rails -v
If the Rails version is less than 4, update it using a following command:

gem update rails --no-ri --no-rdoc
Make sure that all works well by running the application generator command.

rails new railsgirls
cd railsgirls
rails server
Possible errors

Gem::RemoteFetcher error

If you get this error when running rails new railsgirls or gem update rails:

Gem::RemoteFetcher::FetchError: SSL_connect returned=1 errno=0 state=SSLv3 read
server certificate B: certificate verify failed (https://rubygems.org/gems/i18n-
0.6.11.gem)
This means you have an older version of Rubygems and will need to update it manually first verify your Rubygems version

gem -v
If it is lower than 2.2.3 you will need to manually update it:

First download the ruby-gems-update gem. Move the file to c:\\rubygems-update-2.2.3.gem then run:

gem install --local c:\\rubygems-update-2.2.3.gem
update_rubygems --no-ri --no-rdoc
gem uninstall rubygems-update -x
Check your version of rubygems

gem -v
Make sure it is higher than 2.2.3. Re-run the command that was failing previously.

‘x64_mingw’ is not a valid platform` Error

Sometimes you get the following error when running rails server: 'x64_mingw' is not a valid platform If you experience this error after using the RailsInstaller you have to do a small edit to the file Gemfile:

Look at the bottom of the file. You will probably see something like this as one of the last lines in the file: gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]. If you have this line with :x64_mingw, then please delete the :x64_mingw part. In the end it should just say: 'tzinfo-data', platforms: [:mingw, :mswin]

After you did that, please use your Command Prompt again and type bundle update.

2. Install a text editor to edit code files

For the workshop we recommend the text editor Atom.

Download Atom and install it
Download an atom zip file for windows and decompress it.
Copy the folder into your Program Files.
Launch atom in the folder.
If you are using Windows Vista or older versions, you can use another editor Sublime Text 2.

Now you should have a working Ruby on Rails programming setup. Congrats!

3. Update your browser

If you use Internet Explorer, we recommend installing Firefox or Google Chrome.

Open whatbrowser.org and update your browser if you don’t have the latest version.

Setup for Linux

1. Install Rails

To install the Ruby on Rails development environment you just need to copy the line below for your Linux distribution (Ubuntu or Fedora), paste it in the Terminal and press Enter. Enjoy the text flying on the screen; it will take quite some time. Grabbing a refreshing drink before starting is encouraged.

Trên Ubuntu:

```sh
bash < <(curl -sL https://raw.github.com/railsgirls/installation-scripts/master/rails-install-ubuntu.sh)
```

If you are going to use RVM installations with gnome-terminal, you’ll probably need to change it’s default options before you can see and use the right Ruby and Rails versions. Find out how: RVM documentation.

Trên Fedora:

```sh
bash < <(curl -sL https://raw.github.com/railsgirls/installation-scripts/master/rails-install-fedora.sh)
```

Make sure that all works well by running the application generator command.

Make sure that all works well by running the application generator command.

```sh
rails new railsgirls
cd railsgirls
rails server
```

2. Install a text editor to edit code files

For the workshop we recommend the text editor Sublime Text.

Download Sublime Text and install it
3. Update your browser

Open whatbrowser.org and update your browser if you don’t have the latest version.

Now you should have a working Ruby on Rails programming setup. Congrats!

Virtual Machine

Instead of installing all tools on your machine, you can also set up a development environment in a Virtual Machine. Please find all the details here.

Using a Cloud Service

Instead of installing Ruby on Rails and an editor on your computer, you can use a webservice for development. All you need is a browser and an internet connection. This guide explains how to get started with nitrous.io. If you’re using a different service, they may use a different wording - e.g. ‘workspace’ instead of ‘box’, but the process is usually pretty similar.

1. Update your browser

If you use Internet Explorer, we recommend installing Firefox or Google Chrome.

Open whatbrowser.org and update your browser if you don’t have the latest version.

### 2. Tạo tài khoản miễn phí

Tới https://nitrous.io và đăng kí miễn phí.

### 3. Setup a development box / workspace for ruby on rails

Login to your nitrous account
Go to the dashboard by using the green ‘Open dashboard’ button
Create a nitrous box: pick Ruby/Rails from the templates - everything else can stay as is, but you can change the name of your box if you want to
It takes a moment until your box is ready

### 4. Find and restart your development box

If you’ve just created your box, you can probably skip these steps - they’re good to know if you login to nitrous again later
You can always find your nitrous boxes by going to the dashboard or choosing ‘Boxes’ from the top menu
Pick your box from the list of boxes
If you haven’t used a box in a while, it might have been shutdown due to inactivity. If you are informed that your box is not running, restart it using the respective button
When your box is up and running, choose ‘IDE’ in order to start coding

### 5. Coding with your development box

- On the left hand side, you find a file browser where you can navigate your directories and file
- In the middle, you find the editor where you can modify your files
- At the bottom, you find the terminal where you can run commands
- Everything you need is here in you browser window - you do not need to start an editor or terminal anywhere else
- If your following a guide or tutorial, use the commands for Linux even if you are on a Windows computer - your operating system does not matter, since all commands are run on your development box, which is a Linux machine
- If a guide or tutorial asks you to point your browser to something like http://localhost:3000, go to the ‘Preview’ menu and pick ‘Port 3000’
- If, for example, you’re asked to open http://localhost:3000/posts, please append ‘/posts’ manually to the URL that has been opened