__TẠO PLAYLIST VIDEO YOUTUBE VỚI YOUTUBE API__

- sử dụng dịch vụ của Google Developer Console để tạo ứng dụng load 1 list các video trên Youtube.
- để có thể tạo ứng dụng load list các video trên Youtube ta cần
	- lấy được SHA-1 Key của App
	- tạo 1 project trên GDC (Google Developer Console)
		- tạo API Key
		- Edit API Key
	- có được ID của Playlist Youtube (nên tự tạo playlist riêng trên Youtube)
	- lưu ý vấn đề xin quyền INTERNET và cấu hình Gradle để có thể gọi được package Youtube Player
- với App sử dụng phát 1 playlist trên Youtube ta có thể tối ưu việc phát video đến user, tận dụng được Server Youtube lưu trữ Video có sẵn mà không cần thiết lập Server hay Host riêng

___

__TẠO PROJECT CHO APP SẼ SỬ DỤNG DỊCH VỤ CỦA GDC__

- truy cập Google Developer Console [https://console.developers.google.com](https://console.developers.google.com)
- đăng nhập tài khoản google
<img src="/7_login_google.png"> <br/>

- click chọn country và các term của Google API, ta sẽ vào giao diện DASHBOARD của Google Developer Console
<img src="/8_check_terms.png"> <br/>

- copy package name của App
<img src="/9_copy_package_name_app.png"> <br/>

- ở DashBoard của GDC click SELECT A PROJECT
10_click_select_a_project_on_dashboard_of_google_developer_console

- cửa sổ quản lý Project hiện lên, chọn NEW PROJECT
11_click_new_project

- paste package name của project android vào ô project name của GDC project, GDC sẽ tự Generate Project ID (ta có thể tự EDIT lại theo nhu cầu, sau khi CREATE thì không thể thay đổi), sau đó click CREATE
12_paste_package_name_project_into_name_project_field

- sau khi CREATE Project GDC, có thông báo hoàn thành việc tạo Project, click chọn SELECT PROJECT vừa tạo, hoặc click vào mục hiển thị danh sách Project GDC chọn Project để mở
13_select_project_created

- quay trở lại DASHBOARD của Project GDC, click Credentials
14_dashboard_click_credentials

- cửa sổ quản lý Credential xuất hiện, click CREATE CREDENTIAL, chọn API KEY
15_create_credential_api_key

- Popup xuất hiện hiển thị API_KEY vừa được CREATE
16_popup_show_api_key

- CLOSE Popup, click vào tùy chọn Option tiến hành Edit API Key
17_edit_api_key

- ở Application Restrictions, chọn mục Android Apps
18_application_restriction_select_android_app

- mục Restrict usage to your Android Apps click ADD
19_add_restrict_usage_to_your_android_apps

- copy full package name của App
20_copy_full_package_name_app

- paste full package name App vào field Package name của mục Restrict usage to your Android Apps trên Project GDC
21_paste_full_package_name

- để lấy SHA-1 certificate finger print của App, ta cần turn on task list của Gradle
22_turn_on_Gradle_task_list

- mở tab Gradle, double click signingReport để lấy SHA-1 Key
23_double_click_signing_report

- copy SHA-1 Key
24_copy_sha_1_key

- paste SHA-1 Key vào field SHA-1 finger print của Restrict usage to your Android Apps trên Project GDC, click DONE, và SAVE để lưu lại quá trình Edit API Key
25_paste_sha_1_key

- mở Library tab trong Dashboard của Project GDC để Enable các Library cần thiết:
26_open_library

- trong mục library Youtube, ENABLE YouTube Data API V3
27_youtube_data_api_v3

- trong mục library Social, ENABLE Google+ API và Contact API
28_google_plus_api_and_contact_api

- download library Youtube Android Player API để có thể sử dụng giao diện Play Video của Youtube
2_download_youtube_android_player_api

- giải nén folder chứa YoutubeAndroidPlayer API, sau đó copy file
3_giai_nen_copy_file_jar

- paste file jar vào folder libs của Project ở View Project
4_paste_file_jar_vao_folder_libs

- chuột phải vào file jar chọn Add As Library để add library này vào module:app
5_add_as_library

- kết quả sau khi add as library
6_kq_sau_khi_add_as_library

- nếu ``targetApi`` trong thẻ ``application`` của AndroidManifest là Android 11 (API level 30) hoặc cao hơn, việc truy vấn thông tin về các ứng dụng khác được cài đặt trên thiết bị, hệ thống sẽ lọc các thông tin này theo mặc định, được gọi là tính năng LỌC HẠN CHẾ KHẢ NĂNG HIỂN THỊ GÓI, Khả năng hiển thị ứng dụng hạn chế ảnh hưởng đến kết quả trả về của các phương thức cung cấp thông tin về các ứng dụng khác, chẳng hạn như queryIntentActivities(), getPackageInfo() và getInstalledApplications(). Khả năng hiển thị hạn chế cũng ảnh hưởng đến các tương tác rõ ràng với các ứng dụng khác, chẳng hạn như bắt đầu dịch vụ của ứng dụng khác.
- ở đây để sử dụng dịch vụ của Youtube, ta cần khai báo Package cần được hiển thị trong AndroidManifest, bằng cách thêm đoạn code khai báo sau
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    //...

    <queries>
        <intent>
            <action android:name="com.google.android.youtube.api.service.START" />
        </intent>
    </queries>

    //...
</manifest>
```

- vì App sẽ kết nối INTERNET nên phải xin quyền INTERNET trong AndroidManifest
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    // ...
    <uses-permission android:name="android.permission.INTERNET"> </uses-permission>
    // ...
</manifest>
```

___

__TẠO PLAYLIST VIDEO TRÊN YOUTUBE VỚI TÀI KHOẢN GOOGLE__

- đối với App hiển thị 1 Playlist Youtube Video, ta chỉ cần có được ID của Playlist mà không cần phải gọi từng ID Video riêng lẻ để loadVideo
- với ID của Playlist, ta sẽ lấy được JSONObject với ID đó, sau đó phân tích JSONObject để lấy ra từng Video trong Playlist khi user click chọn Video bất kỳ trên Playlist
- ta nên tạo riêng cho mình 1 Playlist để chủ động trong việc quản lý Playlist Video, thay vì lấy Playlist của những user trên Youtube, khi họ xóa Playlist sẽ ảnh hưởng đến App
- để tạo 1 Playlist Video trên Youtube:
    - truy cập Youtube [https://www.youtube.com/](https://www.youtube.com/)
    - Login với tài khoản Google vào Youtube
    - ta sẽ có giao diện Youtube đã đăng nhập như sau
    29_interface_youtube

    - click vào icon user, chọn __Kênh của bạn__
    30_click_kenh_cua_ban

    - giao diện quản lý kênh sẽ xuất hiện nếu đã thực hiện thao tác tạo kênh, sau đó click vào mục Quản Lý Video
    31_giao_dien_quan_ly_kenh

    - trình duyệt sẽ điều hướng đến giao diện của Youtube Studio, click chọn Tạo (để tạo Playlist)
    32_chuyen_huong_den_youtube_studio

    - sau khi click Tạo, click chọn Danh sách phát mới
    33_create_playlist

    - đặt tên cho Playlist, chọn chế độ hiển thị, và click Tạo
    34_named_and_select_mode

    - click thẻ Danh sách phát ta sẽ thấy có 1 Playlist đã được tạo chưa có Video
    35_check_playlist

    - để thêm video vào danh sách, ta có thể upload video lên youtube, hoặc add video của người khác vào Playlist của mình, bằng cách truy cập Youtube, truy cập vào 1 Video hoặc 1 Playlist có sẵn, click menu option và chọn Lưu
    36_select_option_video

    - dù chọn cách nào thì vẫn sẽ có 1 kiểu Popup hiện lên, hiển thị Playlist mà ta đã tạo trên Kênh của bạn, click chọn Playlist cần add Video vào là xong, như vậy là Playlist trên kênh của ta đã có Video
    37_result_saving

    - quay trở lại Youtube Studio, mục Danh sách phát ta có 1 Playlist hiển thị số Video đã được add vào
    38_own_playlist
