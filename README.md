<!-- markdownlint-disable MD033 MD041 MD024 -->
<p align="center">
<a href="https://play.picoctf.org/"><img src="images/picoctf-logo.svg" alt="picoctf-logo"></a>
</p>
<!-- markdownlint-enable MD033 -->

# picoCTF

## WebDecode

> Author: Nana Ama Atombo-Sackey
>
> Do you know how to use the web inspector?\
>
> **Hints**
>
> Use the web inspector on other files included by the web page.\
> The flag may or may not be encoded

### Solution

Truy cập vào URL của thử thách, chúng ta thấy một trang web như sau:

![image](images/webdecode/image-1.png)

Nhấn chọn "ABOUT" và Inspect thì thấy có chuỗi `cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMDJjZGNiNTl9` nằm trong attribute `notify_true`. Chuỗi đó có khả năng là flag được mã hóa:

![image](images/webdecode/image-2.png)

Sử dụng [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnQzWldKZmMzVmpZek56YzJaMWJHeDVYMlF6WXpCa1pXUmZNREpqWkdOaU5UbDk), chúng ta có thể nhận được flag từ chuỗi Base64:

![image](images/webdecode/image-3.png)

### Flag

`picoCTF{web_succ3ssfully_d3c0ded_02cdcb59}`

## Unminify

> Author: Jeffery John
>
> I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!\
>
> **Hints**
>
> Try CTRL+U / ⌘+U in your browser to view the page source. You can also add 'view-source:' before the URL, or try `curl <URL>` in your shell.\
> Minification reduces the size of code, but does not change its functionality.\
> What tools do developers use when working on a website? Many text editors and browsers include formatting.
>
### Solution

Vào thử thách, chúng ta có trang web sau:

![image](images/unminify/image-1.png)

Xem HTML source code, chúng ta lụm được flag:

![image](images/unminify/image-2.png)

### Flag

`picoCTF{pr3tty_c0d3_743d0f9b}`

## IntroToBurp

> Author: Nana Ama Atombo-Sackey & Sabine Gisagara
>
> **Hints**
>
> Try using burpsuite to intercept request to capture the flag.\
> Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.

### Solution

Chúng ta có một trang web đơn giản cho phép đăng ký tài khoản:

![image](images/introtoburp/image-1.png)

Nhập vào thông tin và đăng ký thử:

![image](images/introtoburp/image-2.png)

Sau khi nhấn "Register", chúng ta được chuyển đến trang xác thực 2FA, yêu cầu nhập OTP:

![image](images/introtoburp/image-3.png)

Chúng ta không biết mã OTP là gì nhưng nếu đổi tham số `otp` thành `otp[]` sẽ bypass thành công và nhận được flag:

![image](images/introtoburp/image-4.png)

### Flag

`picoCTF{#0TP_Bypvss_SuCc3$S_2e80f1fd}`

## Bookmarklet

> Author: Jeffery John
>
> Why search for the flag when I can make a bookmarklet to print it for me?
>
> **Hints**
>
> A bookmarklet is a bookmark that runs JavaScript instead of loading a webpage.
> What happens when you click a bookmarklet?
> Web browsers have other ways to run JavaScript too.

### Solution

Vào thử thách, chúng ta có một đoạn code JavaScript:

![image](images/bookmarklet/image-1.png)

Copy đoạn code đó và paste vào tab Console để thực thi, chúng ta nhận được flag:

![image](images/bookmarklet/image-2.png)

### Flag

`picoCTF{p@g3_turn3r_18d2fa20}`

## Local Authority

> Author: LT 'syreal' Jones
>
> Can you get the flag?
>
> **Hints**
>
> How is the password checked on this website?

### Solution

Bắt đầu thử thách, chúng ta có một trang web như sau:

![image](images/local-authority/image-1.png)

Đăng nhập thử với tài khoản `admin:admin` nhưng không thành công:

![image](images/local-authority/image-2.png)

Khi xem HTML source code sẽ thấy có file `secure.js`:

![image](images/local-authority/image-3.png)

Truy cập vào file `secure.js`, chúng ta thấy tài khoản của admin là `admin:strongPassword098765`:

![image](images/local-authority/image-4.png)

Đăng nhập với tài khoản trên, chúng ta có được flag:

![image](images/local-authority/image-5.png)

### Flag

`picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}`

## Inspect HTML

> Author: LT 'syreal' Jones
>
> Can you get the flag?
>
> **Hints**
>
> What is the web inspector in web browsers?

### Solution

Vào thử thách, chúng ta có trang web sau:

![image](images/inspect-html/image-1.png)

Sau khi xem HTML source code, chúng ta sẽ thấy phần comment chứa flag:

![image](images/inspect-html/image-2.png)

### Flag

`picoCTF{1n5p3t0r_0f_h7ml_fd5d57bd}`

## Includes

> Author: LT 'syreal' Jones
>
> Can you get the flag?
>
> **Hints**
>
> Is there more code than what the inspector initially shows?

### Solution

Chúng ta có một trang web như sau:

![image](images/includes/image-1.png)

Khi nhấn "Say hello", một alert xuất hiện nói code này ở một file khác, gợi ý sự tồn tại của một file JavaScript:

![image](images/includes/image-2.png)

Xem HTML source code, chúng ta sẽ thấy có 2 files là `style.css` và `script.js`:

![image](images/includes/image-3.png)

Vào file `style.css`, chúng ta thấy phần đầu của flag:

![image](images/includes/image-4.png)

Và vào file `script.js`, chúng ta lấy được phần flag còn lại:

![image](images/includes/image-5.png)

### Flag

`picoCTF{1nclu51v17y_1of2_f7w_2of2_6edef411}`

## Cookies

> Author: madStacks
>
> Who doesn't love cookies? Try to figure out the best one.\
<http://mercury.picoctf.net:21485/>

### Solution

Vào URL của thử thách, chúng ta có một trang web như sau:

![image](images/cookies/image-1.png)

Nhập luôn chuỗi `snickerdoodle` và nhấn "Search" thì chúng ta vẫn chưa thấy flag đâu:

![image](images/cookies/image-2.png)

Chúng ta được cấp một cookie `name=0`:

![image](images/cookies/image-3.png)

Nếu chúng ta sửa `0` thành `1` vẫn không có flag:

![image](images/cookies/image-4.png)

Vậy, chúng ta sẽ sử dụng Burp Intruder để brute-force tìm ra con số phù hợp:

![image](images/cookies/image-5.png)

"Start attack" và sau chốc lát chờ đợi, với `name=18`, chúng ta có được flag:

![image](images/cookies/image-6.png)

### Flag

`picoCTF{3v3ry1_l0v3s_c00k135_94190c8a}`

## Scavenger Hunt

> Author: madStacks
>
> There is some interesting information hidden around this site <http://mercury.picoctf.net:39698/>. Can you find it?
>
> **Hints**
>
> You should have enough hints to find the files, don't run a brute forcer.

### Solution

Vào URL của thử thách, chúng ta có một trang web như sau:

![image](images/scavenger-hunt/image-1.png)

Xem HTML source code, chúng ta lấy được phần thứ nhất của flag:

![image](images/scavenger-hunt/image-2.png)

Vào file `mycss.css`, chúng ta lấy được phần thứ hai:

![image](images/scavenger-hunt/image-3.png)

Ở file `myjs.js`, phần comment đề cập tới Google, gợi ý trang web có file `robots.txt`:

![image](images/scavenger-hunt/image-4.png)

Vào file `robots.txt`, chúng ta lụm được phần ba của flag:

![image](images/scavenger-hunt/image-5.png)

Do ở trong file `robots.txt` có đề cập đến server Apache và từ `Access` được viết hoa chữ cái `A` nên chúng ta nghĩ tới có file `.htaccess`. Truy cập vào, chúng ta lấy được phần thứ tư:

![image](images/scavenger-hunt/image-6.png)

Ở file `.htaccess` đề cập đến `Mac` và từ `Store` lại được viết hoa chữ cái đầu nên chúng ta sẽ truy cập vào file `.DS_Store` (một file ẩn mà Finder tự động tạo trong các thư mục để lưu trữ thông tin hiển thị của thư mục đó), lụm được phần cuối của flag:

![image](images/scavenger-hunt/image-7.png)

### Flag

`picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_fa04427c}`

## GET aHEAD

> Author: madStacks
>
> Find the flag being held on this server to get ahead of the competition <http://mercury.picoctf.net:34561/>
>
> **Hints**
>
> Maybe you have more than 2 choices\
> Check out tools like Burpsuite to modify your requests and look at the responses

### Solution

Vào URL của thử thách, chúng ta có trang web cho phép lựa chọn màu sắc đỏ hoặc xanh:

![image](images/get-ahead/image-1.png)

Nhấn "Choose Blue" thì màu nền sẽ đổi thành xanh nhưng không có gì đặc biệt:

![image](images/get-ahead/image-2.png)

Tuy nhiên, theo tên của thử thách là `GET aHEAD` với `GET` và `HEAD` được viết in hoa, chúng ta có thể nghĩ tới việc thay đổi request method.

Gửi request với method `HEAD`, chúng ta lụm thành công flag:

![image](images/get-ahead/image-3.png)

### Flag

`picoCTF{r3j3ct_th3_du4l1ty_8f878508}`

## dont-use-client-side

> Author: Alex Fulton/Danny
>
> Can you break into this super secure portal? <https://jupiter.challenges.picoctf.org/problem/29835/> or <http://jupiter.challenges.picoctf.org:29835>
>
> **Hints**
>
> Never trust the client

### Solution

Vào URL của thử thách, chúng ta có một trang web để nhập credentials:

![image](images/dont-use-client-side/image-1.png)

Khi xem HTML source code, chúng ta sẽ có các mảnh của flag, công việc bây giờ là cần ghép chúng lại sao cho phù hợp:

![image](images/dont-use-client-side/image-2.png)

### Flag

`picoCTF{no_clients_plz_7723ce}`

## logon

> Author: bobson
>
> The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? <https://jupiter.challenges.picoctf.org/problem/13594/> or <http://jupiter.challenges.picoctf.org:13594>
>
> **Hints**
>
> Hmm it doesn't seem to check anyone's password, except for Joe's?

### Solution

Vào URL của thử thách, chúng ta có một trang web cho phép đăng nhập:

![image](images/logon/image-1.png)

Chúng ta có thể đăng nhập thành công với tài khoản `admin:admin`:

![image](images/logon/image-2.png)

Vẫn chưa thấy flag, kiểm tra sẽ có một cookie `admin` với giá trị `False` được chỉ định:

![image](images/logon/image-3.png)

Vậy, chúng ta sẽ sửa giá trị của cookie `admin` thành `True`:

![image](images/logon/image-4.png)

Tải lại trang web và chúng ta thấy được flag:

![image](images/logon/image-5.png)

### Flag

`picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}`

## Insp3ct0r

> Author: zaratec/danny
>
> Kishor Balan tipped us off that the following code may need inspection: <https://jupiter.challenges.picoctf.org/problem/44924/> or <http://jupiter.challenges.picoctf.org:44924>
>
> **Hints**
>
> How do you inspect web code on a browser?\
> There's 3 parts

### Solution

Vào URL, chúng ta có một trang web đơn giản:

![image](images/insp3ct0r/image-1.png)

Xem HTML source code, chúng ta thấy phần thứ nhất của flag:

![image](images/insp3ct0r/image-2.png)

Truy cập vào file `mycss.css`, chúng ta lụm được phần thứ hai:

![image](images/insp3ct0r/image-3.png)

Và phần thứ ba của flag nằm ở trong file `myjs.js`:

![image](images/insp3ct0r/image-4.png)

### Flag

`picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?f10be399}`

## where are the robots

> Author: zaratec/Danny
>
> Can you find the robots? <https://jupiter.challenges.picoctf.org/problem/36474/> or <http://jupiter.challenges.picoctf.org:36474>
>
> *Hints*
>
> What part of the website could tell you where the creator doesn't want you to look?

### Solution

Vào thử thách, chúng ta thấy trang web sau:

![image](images/where-are-the-robots/image-1.png)

Nó hỏi `robots` ở đâu nên chúng ta có thể nghĩ tới trang web có file `robots.txt`. Truy cập vào, chúng ta thấy một file `477ce.html` được chỉ định:

![image](images/where-are-the-robots/image-2.png)

Vào file `477ce.html`, chúng ta lụm được flag:

![image](images/where-are-the-robots/image-3.png)

### Flag

`picoCTF{ca1cu1at1ng_Mach1n3s_477ce}`

## Trickster

> Author: Junias Bonou
>
> I found a web app that can help process images: PNG images only!

### Solution

Vào URL của thử thách, chúng ta có một trang web cho phép tải lên file:

![image](images/trickster/image-1.png)

Thử tải lên một file ảnh để kiểm tra:

![image](images/trickster/image-2.png)

File chúng ta tải lên sẽ được lưu ở `uploads`:

![image](images/trickster/image-3.png)

Bên dưới là POST request khi chúng ta tải lên file. Chú ý response headers, chúng ta thấy server Apache với PHP phiên bản 8.0.30:

![image](images/trickster/image-4.png)

Vậy chúng ta sẽ tải lên một webshell PHP với tên `shell.php`. Thêm payload sau vào nội dung file để có thể thực hiện RCE:

```php
<?=`$_GET[0]`?>
```

Gửi request, chúng ta thấy thông báo lỗi tên file không chứa `.png`:

![image](images/trickster/image-5.png)

Chúng ta có thể bypass bằng cách sử dụng tên file là `shell.png.php`. Tuy nhiên, lại có một thông báo lỗi mới là file không phải ảnh PNG hợp lệ:

![image](images/trickster/image-6.png)

Do đó, chúng ta sẽ thêm `PNG` vào nội dung file để bypass và tải lên webshell thành công:

![image](images/trickster/image-7.png)

Giờ truy cập tới `/uploads/shell.png.php?0`, chúng ta có thể thực thi lệnh.

Với lệnh `ls ..`, chúng ta thấy có một file đáng nghi là `GQ4DOOBVMMYGK.txt`:

![image](images/trickster/image-8.png)

Đọc file đó với lệnh `cat ../G*`, chúng ta lụm flag thành công:

![image](images/trickster/image-9.png)

### Flag

`picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_48785c0e}`

## No Sql Injection

> Author: NGIRIMANA Schadrack
>
> Can you try to get access to this website to get the flag?
> You can download the source [here](sources/no-sql-injection.zip).
>
> **Hints**
>
> Not only SQL injection exist but also NonSQL injection exists.\
> Make sure you look at everything the server is sending back.

### Solution

Chúng ta có một trang web cho phép đăng nhập:

![image](images/no-sql-injection/image-1.png)

Cùng phân tích source code được cung cấp để hiểu rõ cách thực hoạt động của trang web:

```text
.
├── admin.html
├── index.html
├── package.json
└── server.js
```

Ở file `server.js` là code xử lý của server:

```js
const express = require("express");
const bodyParser = require("body-parser");
const mongoose = require("mongoose");
const { MongoMemoryServer } = require("mongodb-memory-server");
const path = require("path");
const crypto = require("crypto");

const app = express();
const port = process.env.PORT | 3000;

// Middleware to parse JSON data
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// User schema and model
const userSchema = new mongoose.Schema({
  email: { type: String, required: true, unique: true },
  firstName: { type: String, required: true },
  lastName: { type: String, required: true },
  password: { type: String, required: true },
  token: { type: String, required: false, default: "{{Flag}}" },
});

const User = mongoose.model("User", userSchema);

// Initialize MongoMemoryServer and connect to it
async function startServer() {
  try {
    const mongoServer = await MongoMemoryServer.create();
    const mongoUri = mongoServer.getUri();
    await mongoose.connect(mongoUri);

    // Store initial user
    const initialUser = new User({
      firstName: "pico",
      lastName: "player",
      email: "picoplayer355@picoctf.org",
      password: crypto.randomBytes(16).toString("hex").slice(0, 16),
    });
    await initialUser.save();

    // Serve the HTML form
    app.get("/", (req, res) => {
      res.sendFile(path.join(__dirname, "index.html"));
    });

    // Serve the admin page
    app.get("/admin", (req, res) => {
      res.sendFile(path.join(__dirname, "admin.html"));
    });

    // Handle login form submission with JSON
    app.post("/login", async (req, res) => {
      const { email, password } = req.body;

      try {
        const user = await User.findOne({
          email:
            email.startsWith("{") && email.endsWith("}")
              ? JSON.parse(email)
              : email,
          password:
            password.startsWith("{") && password.endsWith("}")
              ? JSON.parse(password)
              : password,
        });

        if (user) {
          res.json({
            success: true,
            email: user.email,
            token: user.token,
            firstName: user.firstName,
            lastName: user.lastName,
          });
        } else {
          res.json({ success: false });
        }
      } catch (err) {
        res.status(500).json({ success: false, error: err.message });
      }
    });

    app.listen(port, () => {
    });
  } catch (err) {
    console.error(err);
  }
}

startServer().catch((err) => console.error(err));

```

Để lấy được flag, chúng ta cần phải đăng nhập thành công vào email `picoplayer355@picoctf.org`. Tuy nhiên, chúng ta lại không biết mật khẩu của người dùng này bởi nó được tạo ngẫu nhiên.

Chúng ta cần tập trung vào đoạn code xử lý tại route `/login`:

```js
app.post("/login", async (req, res) => {
      const { email, password } = req.body;

      try {
        const user = await User.findOne({
          email:
            email.startsWith("{") && email.endsWith("}")
              ? JSON.parse(email)
              : email,
          password:
            password.startsWith("{") && password.endsWith("}")
              ? JSON.parse(password)
              : password,
        });

        if (user) {
          res.json({
            success: true,
            email: user.email,
            token: user.token,
            firstName: user.firstName,
            lastName: user.lastName,
          });
        } else {
          res.json({ success: false });
        }
      } catch (err) {
        res.status(500).json({ success: false, error: err.message });
      }
    });
```

Trong trường hợp giá trị của tham số `email` hoặc `password` mà bắt đầu với `{` và kết thúc với `}` thì nó sẽ được chuyển thành `object` bởi hàm `JSON.parse()`. Cộng thêm việc server sử dụng `mongoose` nên đó chính là điều kiện lý tưởng để khai thác lỗi NoSQL Injection.

Do đó, chúng ta sẽ có thể sử dụng payload sau để gửi request. Thực hiện đăng nhập với điều kiện `email` là `picoplayer355@picoctf.org` và `password` không phải là `xxx`:

```json
{
  "email":"picoplayer355@picoctf.org",
  "password":"{\"$ne\":\"xxx\"}"
}
```

Gửi request và lụm thành công flag:

![image](images/no-sql-injection/image-2.png)

### Flag

`picoCTF{jBhD2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_25ba4de1}`

## SOAP

> Author: Geoffrey Njogu
>
> The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?
>
> **Hints**
>
> XML external entity Injection

### Solution

Vào URL của thử thách, chúng ta có trang web sau:

![image](images/soap/image-1.png)

Khi nhấn "Details", chúng ta thấy một thông báo xuất hiện ở phía dưới:

![image](images/soap/image-2.png)

Kiểm tra request, chúng ta sẽ thấy đó là một POST request với dữ liệu XML được gửi đi trong body:

![image](images/soap/image-3.png)

Chúng ta có thể nghĩ ngay tới việc khai thác lỗ hổng XXE. Theo như mô tả, mục tiêu của chúng ta là đọc file `/etc/passwd` nên sử dụng payload sau:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE abc [<!ENTITY etc SYSTEM 'file:///etc/passwd'>]>
<data>
    <ID>
      &etc;
    </ID>
</data>
```

Gửi đi request, chúng ta thấy flag nằm trong response:

![image](images/soap/image-4.png)

### Flag

`picoCTF{XML_3xtern@l_3nt1t1ty_e5f02dbf}`

## More SQLi

> Author: Mubarak Mikail
>
> Can you find the flag on this website.
>
> **Hints**
>
> SQLiLite

### Solution

Chúng ta có một trang web cho phép đăng nhập như sau:

![image](images/more-sqli/image-1.png)

Thử đăng nhập với tài khoản `admin:admin`, chúng ta thấy trang web hiển thị ra câu truy vấn SQL:

![image](images/more-sqli/image-2.png)

Có thể thấy cả 2 giá trị mà chúng ta nhập đang được truyền thẳng vào trong cặp dấu `'`.

Lỗi server 500 khi chúng ta thực hiện đăng nhập với thông tin sai:

![image](images/more-sqli/image-3.png)

Chúng ta sẽ khai thác SQL Injection với payload cơ bản sau để khiến điều kiện ở mệnh đề `WHERE` đúng:

```text
username=admin&password=' OR 1=1--
```

Gửi request, chúng ta lấy được flag:

![image](images/more-sqli/image-4.png)

### Flag

`picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_62aa7500}`

## MatchTheRegex

> Author: Sunday Jacob Nwanyim
>
> How about trying to match a regular expression
>
> **Hints**
>
> Access the webpage and try to match the regular expression associated with the text field

### Solution

Chúng ta có một trang web cho phép nhập vào dữ liệu:

![image](images/matchtheregex/image-1.png)

Nhập thử "a", chúng ta nhận thông báo kết quả không khớp:

![image](images/matchtheregex/image-2.png)

Xem đoạn code JavaScript bên dưới, chúng ta có thể hiểu là server sẽ cho phép nhập vào một chuỗi regex, nếu nó có thể khớp với chuỗi flag thì chúng ta nhận được flag:

![image](images/matchtheregex/image-3.png)

Vậy nhập vào đoạn regex `picoCTF{.*}` với `.*` để khớp tất cả các ký tự ngoại trừ dấu xuống dòng, chúng ta có thể lụm flag:

![image](images/matchtheregex/image-4.png)

### Flag

`picoCTF{succ3ssfully_matchtheregex_2375af79}`

## findme

> Author: Geoffrey Njogu
>
> Help us test the form by submiting the username as `test` and password as `test!`
>
> **Hints**
>
> any redirections?

### Solution

Chúng ta có một trang web cho phép nhập vào thông tin tài khoản để kiểm tra:

![image](images/findme/image-1.png)

Sau khi đăng nhập với tài khoản `test:test!` được đề cập trong mô tả, chúng ta thấy rằng bị redirect mấy lần và tới trang sau:

![image](images/findme/image-2.png)

Kiểm tra HTTP history trong Burp Suite, chúng ta thấy flag được chia thành 2 phần và mã hóa Base64 rồi truyền tới tham số `id`, bên dưới là phần đầu:

![image](images/findme/image-3.png)

Và phần cuối của flag:

![image](images/findme/image-4.png)

### Flag

`picoCTF{proxies_all_the_way_a0fe074f}`

## SQLiLite

> Author: Mubarak Mikail
>
> Can you login to this website?
>
> **Hints**
>
> `admin` is the user you want to login as.

### Solution

Truy cập vào URL của thử thách, chúng ta thấy một giao diện đăng nhập như sau:

![image](images/sqlilite/image-1.png)

Mục tiêu của chúng ta là đăng nhập với người dùng `admin`, thử đăng nhập với tài khoản `admin:admin`, chúng ta thấy thông báo đăng nhập thất bại kèm theo câu truy vấn xuất hiện:

![image](images/sqlilite/image-2.png)

Cả tên người dùng và mật khẩu đều được truyền vào cặp dấu `'` nên có thể khai thác SQL Injection tại đây.

Chúng ta sẽ chỉ cần nhập tên người dùng là `admin'--` để bypass thành công:

![image](images/sqlilite/image-3.png)

Đã đăng nhập thành công nhưng flag ở đâu?

![image](images/sqlilite/image-4.png)

Xem HTML source code, chúng ta thấy flag:

![image](images/sqlilite/image-5.png)

### Flag

`picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}`

## SQL Direct

> Author: Mubarak Mikail / LT 'syreal' Jones
>
> Connect to this PostgreSQL server and find the flag!\
> `psql -h saturn.picoctf.net -p 62220 -U postgres pico`\
> Password is `postgres`

### Solution

Chúng ta sẽ sử dụng luôn webshell trên pico để chạy lệnh kết nối tới PostgreSQL server.

Lệnh xem các bảng trong database hiện tại:

```text
\dt
```

Lấy tất cả các bản ghi từ bảng `flags` với câu truy vấn:

```sql
SELECT * FROM flags;
```

![image](images/sql-direct/image-1.png)

### Flag

`picoCTF{L3arN_S0m3_5qL_t0d4Y_31fd14c0}`

## Secrets

> Author: Geoffrey Njogu
>
> We have several pages hidden. Can you find the one with the flag?
>
> **Hints**
>
> folders folders folders

### Solution

Vào thử thách, chúng ta có trang web sau:

![image](images/secrets/image-1.png)

Xem HTML source code, chúng ta thấy có một đường dẫn đáng nghi `secret/assets/DX1KYM.jpg`:

![image](images/secrets/image-2.png)

Khi gửi request tới `/secret/`, chúng ta lại thấy có thư mục `hidden`:

![image](images/secrets/image-3.png)

Gửi request tới `/secret/hidden/`, chúng ta thấy có thư mục tiếp theo là `superhidden`:

![image](images/secrets/image-4.png)

Và khi request tới `/secret/hidden/superhidden/`, chúng ta lụm thành công flag:

![image](images/secrets/image-5.png)

### Flag

`picoCTF{succ3ss_@h3n1c@10n_39849bcf}`

## Search source

>Author: Mubarak Mikail
>
> The developer of this website mistakenly left an important artifact in the website source, can you find it?
>
> **Hints**
>
> How could you mirror the website on your local machine so you could use more powerful tools for searching?

### Solution

Chúng ta có trang web như sau:

![image](images/search-source/image-1.png)

Xem HTML source code, chúng ta đi vào file `css/style.css` sẽ thấy có flag:

![image](images/search-source/image-2.png)

### Flag

`picoCTF{1nsp3ti0n_0f_w3bpag3s_8de925a7}`

## Roboto Sans

> Author: Mubarak Mikail
>
> The flag is somewhere on this web application not necessarily on the website. Find it.

### Solution

Vào URL của thử thách, chúng ta có một trang web như sau:

![image](images/roboto-sans/image-1.png)

Truy cập vào file `robots.txt`, chúng ta thấy có một đoạn chuỗi Base64 khả nghi. Khi decode thì thấy đường dẫn `js/myfile.txt`:

![image](images/roboto-sans/image-2.png)

Truy cập tới `js/myfile.txt`, chúng ta có thể lấy flag thành công:

![image](images/roboto-sans/image-3.png)

### Flag

`picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}`

## Power Cookie

> Author: LT 'syreal' Jones
>
> Can you get the flag?
>
> **Hints**
>
> Do you know how to modify cookies?

### Solution

Vào thử thách, chúng ta có trang web đơn giản sau:

![image](images/power-cookie/image-1.png)

Khi nhấn "Continue as guest", chúng ta nhận một lời xin lỗi:

![image](images/power-cookie/image-2.png)

Nếu kiểm tra cookies, chúng ta sẽ thấy có cookie `isAdmin` với giá trị `0`:

![image](images/power-cookie/image-3.png)

Vậy chúng ta sẽ đổi `0` thành `1`:

![image](images/power-cookie/image-4.png)

Tải lại trang web, chúng ta nhận được flag:

![image](images/power-cookie/image-5.png)

### Flag

`picoCTF{gr4d3_A_c00k13_5d2505be}`

## Forbidden Paths

> Author: LT 'syreal' Jones
>
> Can you get the flag?
> We know that the website files live in `/usr/share/nginx/html/` and the flag is at `/flag.txt` but the website is filtering absolute file paths. Can you get past the filter to read the flag?

### Solution

Vào thử thách, chúng ta có trang web cho phép đọc file:

![image](images/forbidden-paths/image-1.png)
Đọc thử file `oliver-twist.txt`:

![image](images/forbidden-paths/image-2.png)

Bên dưới là POST request tới `/read.php` để thực hiện đọc file:

![image](images/forbidden-paths/image-3.png)

Chúng ta thử thay đổi giá trị của tham số `filename` thành `/etc/passwd` để đọc file này. Tuy nhiên, không thể đọc được:

![image](images/forbidden-paths/image-4.png)

Đúng theo mô tả, chúng ta không được sử dụng đường dẫn tuyệt đối để đọc file.

Vậy chúng ta có thể bypass bằng cách sử dụng `../`:

![image](images/forbidden-paths/image-5.png)

Và đọc flag thành công với payload:

```text
../../../flag.txt
```

![image](images/forbidden-paths/image-6.png)

### Flag

`picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}`

## JAuth

> Author: Geoffrey Njogu
>
> Most web application developers use third party components without testing their security. Some of the past affected companies are:
>
> - Equifax (a US credit bureau organization) - breach due to unpatched Apache Struts web framework CVE-2017-5638
> - Mossack Fonesca (Panama Papers law firm) breach - unpatched version of Drupal CMS used
> - VerticalScope (internet media company) - outdated version of vBulletin forum software used
>
> Can you identify the components and exploit the vulnerable one?\
> The website is running here. Can you become an admin?\
> You can login as `test` with the password `Test123!` to get started.
>
> **Hints**
>
> Use the web browser tools to check out the JWT cookie.\
> The JWT should always have two (2) . separators.

### Solution

Vào thử thách, chúng ta có một trang web cho phép đăng nhập như sau:

![image](images/jauth/image-1.png)

Đăng nhập thành công với tài khoản được cung cấp `test:Test123!` nhưng không thấy có gì xuất hiện:

![image](images/jauth/image-2.png)

Chúng ta kiểm tra request tới `/private`, thấy có một cookie `token` là JWT:

![image](images/jauth/image-3.png)

Xem trong phần payload của chuỗi JWT có chứa `"role":"user"`:

![image](images/jauth/image-4.png)

Theo như mô tả cũng như tìm kiếm thông tin liên quan, chúng ta xác định có thể khai thác JWT sử dụng None Algorithm.

Trước tiên, thay giá trị của `"role"` thành `"admin"`:

![image](images/jauth/image-5.png)

Chúng ta đổi giá trị của `"alg"` thành `"none"`:

![image](images/jauth/image-6.png)

Xóa đi phần signature nhưng cần giữ lại dấu `.` ở cuối:

![image](images/jauth/image-7.png)

Cuối cùng, gửi request chúng ta thấy flag:

![image](images/jauth/image-8.png)

### Flag

`picoCTF{succ3ss_@u7h3nt1c@710n_72bf8bd5}`

## caas

> Author: BrownieInMotion
>
> Now presenting cowsay as a service
>
> [index.js](sources/caas/index.js)

### Solution

Vào thử thách, chúng ta có một trang web sau:

![image](images/caas/image-1.png)

Phân tích source code được cung cấp, chúng ta nhận thấy ngay lỗ hổng OS Command Injection tồn tại ở tham số `message` trong path. Giá trị của tham số `message` được truyền vào làm đối số của lệnh `/usr/games/cowsay`:

```js
...
app.get('/cowsay/:message', (req, res) => {
  exec(`/usr/games/cowsay ${req.params.message}`, {timeout: 5000}, (error, stdout) => {
    if (error) return res.status(500).end();
    res.type('txt').send(stdout).end();
  });
});
...
```

Vậy chúng ta sẽ sử dụng payload `$(ls)`, xác định được có file `falg.txt` ở thư mục hiện tại:

![image](images/caas/image-2.png)

Đọc file đó với payload `$(cat${IFS}falg.txt)`, trong payload này, chúng ta dùng `${IFS}` để tránh khoảng trắng khiến lệnh không thể thực thi:

![image](images/caas/image-4.png)

Ngoài ra, chúng ta cũng có thể sử dụng một số payload khác:

![image](images/caas/image-4.png)

![image](images/caas/image-5.png)

### Flag

`picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`
