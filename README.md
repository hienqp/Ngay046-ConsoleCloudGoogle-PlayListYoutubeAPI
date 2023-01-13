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
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/7_login_google.png"> <br/>

- click chọn country và các term của Google API, ta sẽ vào giao diện DASHBOARD của Google Developer Console
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/8_check_terms.png"> <br/>

- copy package name của App
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/9_copy_package_name_app.png"> <br/>

- ở DashBoard của GDC click SELECT A PROJECT
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/10_click_select_a_project_on_dashboard_of_google_developer_console.png"> <br/>


- cửa sổ quản lý Project hiện lên, chọn NEW PROJECT
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/11_click_new_project.png"> <br/>


- paste package name của project android vào ô project name của GDC project, GDC sẽ tự Generate Project ID (ta có thể tự EDIT lại theo nhu cầu, sau khi CREATE thì không thể thay đổi), sau đó click CREATE
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/12_paste_package_name_project_into_name_project_field.png"> <br/>


- sau khi CREATE Project GDC, có thông báo hoàn thành việc tạo Project, click chọn SELECT PROJECT vừa tạo, hoặc click vào mục hiển thị danh sách Project GDC chọn Project để mở
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/13_select_project_created.png"> <br/>


- quay trở lại DASHBOARD của Project GDC, click Credentials
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/14_dashboard_click_credentials.png"> <br/>


- cửa sổ quản lý Credential xuất hiện, click CREATE CREDENTIAL, chọn API KEY
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/15_create_credential_api_key.png"> <br/>


- Popup xuất hiện hiển thị API_KEY vừa được CREATE
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/16_popup_show_api_key.png"> <br/>


- CLOSE Popup, click vào tùy chọn Option tiến hành Edit API Key
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/17_edit_api_key.png"> <br/>


- ở Application Restrictions, chọn mục Android Apps
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/18_application_restriction_select_android_app.png"> <br/>


- mục Restrict usage to your Android Apps click ADD
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/19_add_restrict_usage_to_your_android_apps.png"> <br/>


- copy full package name của App
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/20_copy_full_package_name_app.png"> <br/>


- paste full package name App vào field Package name của mục Restrict usage to your Android Apps trên Project GDC
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/21_paste_full_package_name.png"> <br/>


- để lấy SHA-1 certificate finger print của App, ta cần turn on task list của Gradle
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/22_turn_on_Gradle_task_list.png"> <br/>


- mở tab Gradle, double click signingReport để lấy SHA-1 Key
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/23_double_click_signing_report.png"> <br/>


- copy SHA-1 Key
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/24_copy_sha_1_key.png"> <br/>


- paste SHA-1 Key vào field SHA-1 finger print của Restrict usage to your Android Apps trên Project GDC, click DONE, và SAVE để lưu lại quá trình Edit API Key
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/25_paste_sha_1_key.png"> <br/>


- mở Library tab trong Dashboard của Project GDC để Enable các Library cần thiết:
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/26_open_library.png"> <br/>


- trong mục library Youtube, ENABLE YouTube Data API V3
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/27_youtube_data_api_v3.png"> <br/>


- trong mục library Social, ENABLE Google+ API và Contact API
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/28_google_plus_api_and_contact_api.png"> <br/>


- download library Youtube Android Player API để có thể sử dụng giao diện Play Video của Youtube
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/2_download_youtube_android_player_api.png"> <br/>


- giải nén folder chứa YoutubeAndroidPlayer API, sau đó copy file
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/3_giai_nen_copy_file_jar.png"> <br/>


- paste file jar vào folder libs của Project ở View Project
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/4_paste_file_jar_vao_folder_libs.png"> <br/>


- chuột phải vào file jar chọn Add As Library để add library này vào module:app
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/5_add_as_library.png"> <br/>


- kết quả sau khi add as library
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/6_kq_sau_khi_add_as_library.png"> <br/>


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
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/29_interface_youtube.png"> <br/>
    

    - click vào icon user, chọn __Kênh của bạn__
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/30_click_kenh_cua_ban.png"> <br/>
    

    - giao diện quản lý kênh sẽ xuất hiện nếu đã thực hiện thao tác tạo kênh, sau đó click vào mục Quản Lý Video
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/31_giao_dien_quan_ly_kenh.png"> <br/>
    

    - trình duyệt sẽ điều hướng đến giao diện của Youtube Studio, click chọn Tạo (để tạo Playlist)
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/32_chuyen_huong_den_youtube_studio.png"> <br/>
    

    - sau khi click Tạo, click chọn Danh sách phát mới
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/33_create_playlist.png"> <br/>
    

    - đặt tên cho Playlist, chọn chế độ hiển thị, và click Tạo
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/34_named_and_select_mode.png"> <br/>
    

    - click thẻ Danh sách phát ta sẽ thấy có 1 Playlist đã được tạo chưa có Video
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/35_check_playlist.png"> <br/>
    

    - để thêm video vào danh sách, ta có thể upload video lên youtube, hoặc add video của người khác vào Playlist của mình, bằng cách truy cập Youtube, truy cập vào 1 Video hoặc 1 Playlist có sẵn, click menu option và chọn Lưu
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/36_select_option_video.png"> <br/>
    

    - dù chọn cách nào thì vẫn sẽ có 1 kiểu Popup hiện lên, hiển thị Playlist mà ta đã tạo trên Kênh của bạn, click chọn Playlist cần add Video vào là xong, như vậy là Playlist trên kênh của ta đã có Video
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/37_result_saving.png"> <br/>
    

    - quay trở lại Youtube Studio, mục Danh sách phát ta có 1 Playlist hiển thị số Video đã được add vào
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/38_own_playlist.png"> <br/>


    - click vào playlist đã tạo, ở trên url dãy ký tự phía sau ``https://www.youtube.com/playlist?list=`` chính là ID_PLAYLIST của playlist ta đã tạo
    <img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/39_get_id_playlist.png"> <br/>


___

__TẠO CLASS CONFIG CHỨA THÔNG TIN CẦN XỬ LÝ CHO APP__

- ta tạo class Config chứa:
    - YOUTUBE_API_KEY
    - YOUTUBE_PLAYLIST_ID

<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/40_class_config.png"> <br/>


- ở MainActivity ta khai báo khởi tạo object Config để thuận tiện việc lấy các thông số cần thiết cho logic của App
```java
public class MainActivity extends AppCompatActivity {
    Config config;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        config = new Config();      
    }
}
```

___

__GET JSON OBJECT PLAYLIST VIDEO YOUTUBE TỪ API_KEY VÀ PLAYLIST_ID__

- ta đã có:
    - YOUTUBE_API_KEY
    - đã Enable Contact API, Youtube Data API V3, Google+ API
    - đã Create 1 Playlist Youtube Video
- tiếp theo, để App có thể load Playlist này về, ta sẽ load playlist về bằng format JSON, tức là cả playlist sẽ được App đọc bằng format JSON
- truy cập link [https://developers.google.com/youtube/v3/docs/playlistItems/list](https://developers.google.com/youtube/v3/docs/playlistItems/list), trong mục Try this method, nhập ID của playlist ta đã tạo trên kênh Youtube vào field playlistID
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/41_get_link_load_json_playlist.png"> <br/>

- ở mục Try this method, sau khi nhập playlistID, kéo xuống phía dưới, click button SHOW CODE để xem đường link dùng để lấy Playlist với ID đã nhập về App theo format JSONObject
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/42_show_link.png"> <br/>

- 1 Popup xuất hiện, trong tag ``cURL`` ta click vào button copy
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/43_copy_link.png"> <br/>

- paste nội dung vừa copy vào file txt để copy nội dung cần thiết, ta chỉ lấy đường dẫn URL chứa playlistID và đoạn chuỗi dùng để paste API_KEY vào
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/44_paste_txt.png"> <br/>

- copy URL cần để get JSONObject từ playlistID và API_KEY và paste vào file ``Config.java``, định nghĩa 1 method trả về String là URL dùng để get JSONObject từ playlistID và API_KEY
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/45_create_method_get_json_in_config.png"> <br/>

- để kiểm tra trước code JSONObject có hoạt động hay không, trước tiên playlist video phải để mode công khai (public), quay trở lại đường link [https://developers.google.com/youtube/v3/docs/playlistItems/list](https://developers.google.com/youtube/v3/docs/playlistItems/list), sau khi nhập playlistID, bên cạnh button SHOW CODE, còn có button EXECUTE, click EXECUTE để xem code JSON được trả về
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/46_preview_json_code.png"> <br/>


- CtrlA tất cả paste vào JSONFormatter ta sẽ có 
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/47_jsonformatter.png"> <br/>

- ta thấy ở JSONObject trả về, số lượng ``items`` trả về chỉ có 5 item, trong khi playlist ta có 9 item
- đồng thời ta cũng cần trả về name và thumbnail (hình nhỏ) của mỗi video item
- quay trở lại [https://developers.google.com/youtube/v3/docs/playlistItems/list](https://developers.google.com/youtube/v3/docs/playlistItems/list) trong mục Try this method
    - ở field ``maxResults`` ta nhập 50 (tối đa chỉ cho hiển thị 50 item mỗi page)
    - ở field ``part`` ta nhập __snippet__
    - ở field ``playlistId`` vẫn nhập playlist id như bình thường
    - click SHOW CODE, copy code paste vào file txt ta thấy giữa __playlistItems?__ và __playlistId__ xuất hiện chuỗi __part=snippet&maxResults=50&__, tiến hành chỉnh sửa lại ở file __Config.java__ như sau 
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/48_modify_maxresult_playlist.png"> <br/>


___

__SỬ DỤNG API VOLLEY ĐỂ ĐỌC FILE JSON CỦA PLAYLIST YOUTUBE__

- ta sẽ sử dụng API Volley để đọc file JSONObject, truy cập [https://google.github.io/volley/](https://google.github.io/volley/), copy đoạn code ``implementation`` API Volley paste vào tag ``dependencies`` trong Gradle App và click ``Sync Now``

```js
dependencies {

    // ...
    implementation 'com.android.volley:volley:1.2.1'
}
```

- quay trở lại ``MainActivity``, ta định nghĩa 1 method dùng để parse URL JSONObject từ Youtube
```java
public class MainActivity extends AppCompatActivity {
    Config config;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        config = new Config();

        getJsonObjectYoutube(config.getPlaylistJSONObject());
    }

    private void getJsonObjectYoutube(String urlGetJson) {
        RequestQueue requestQueue = Volley.newRequestQueue(this);

        JsonObjectRequest jsonObjectRequest = new JsonObjectRequest(
                Request.Method.GET,
                urlGetJson,
                null,
                new Response.Listener<JSONObject>() {
                    @Override
                    public void onResponse(JSONObject response) {
                        Toast.makeText(MainActivity.this, response.toString(), Toast.LENGTH_SHORT).show();
                    }
                },
                new Response.ErrorListener() {
                    @Override
                    public void onErrorResponse(VolleyError error) {
                        Toast.makeText(MainActivity.this, "Lỗi !!!", Toast.LENGTH_SHORT).show();
                    }
                });

        requestQueue.add(jsonObjectRequest);
    }
}
```

- kết quả nếu thành công, App sẽ Toast nội dung ``response`` trả về là code JSONObject như sau
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/49_success_toast_json_object.png"> <br/>

___

__PARSE JSON OBJECT YOUTUBE PLAYLIST NHẬN ĐƯỢC__

- như vậy, ta đã GET được JSONObject Youtube Playlist, bây giờ ta sẽ tiến hành Parse (phân giải) nó cụ thể, quay trở lại JSONFormatter, copy và paste code JSON mới nhất với maxResult=50 và part=snippet (sau khi chỉnh sửa) ta sẽ nhìn thấy cụ thể cấu trúc của file JSONObject này như sau
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/50_structure_json_object_on_jsonformatter.png"> <br/>

- như kết quả phân tách từ JSONFormatter, ta thấy kết quả mà ta GET về 1 JSONObject có cấu trúc như sau:
    - Object chứa 4 thành phần
        - String kind
        - String etag
        - Array items chứa 4 thành phần
            - String kind
            - String etag
            - String id (id của item không phải của Video)
            - Object snippet chứa 11 thành phần, trong đó có thành phần quan trọng là videoId
                - publishedAt
                - channelId
                - title
                - description
                - thumbnails
                    - medium
                - channelTitle
                - playlistId
                - position
                - resourceId
                    - kind
                    - videoId (ID của VIDEO, đây là nội dung cần thiết để play video trong playlist)
                - videoOwnerChannelTitle
                - videoOwnerChannelId
        - Object pageInfo chứa 2 thành phần
            - String totalResults
            - String resultsPerPage

- khi khởi tạo đối tượng __JsonObjectRequest__ kết quả trả về là JSONObject mà ta đã Toast thành công, như vậy ta đã có JSONObject của Playlist, bây giờ ta tiến hành lấy ra từng thành phần trong JSONObject này ở từng phân cấp
    - array items
        - object snippet từ items
            - string title từ snippet
            - object thumbnails từ snippet
                - object medium từ thumbnails
                    - string url từ medium
            - object resourceId từ snippet
                - string videoId từ resourceId

- logic get các thành phần JSON cần thiết trong MainActivity
```java
public class MainActivity extends AppCompatActivity {
    Config config;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        config = new Config();

        getJsonObjectYoutube(config.getPlaylistJSONObject());
    }

    private void getJsonObjectYoutube(String urlGetJson) {
        RequestQueue requestQueue = Volley.newRequestQueue(this);

        JsonObjectRequest jsonObjectRequest = new JsonObjectRequest(
                Request.Method.GET,
                urlGetJson,
                null,
                new Response.Listener<JSONObject>() {
                    @Override
                    public void onResponse(JSONObject response) {
                        try {
                            JSONArray Items = response.getJSONArray("items");

                            String titleVideo = "", urlImage = "", videoId = "";

                            for (int i = 0; i < Items.length(); i++) {
                                JSONObject item = Items.getJSONObject(i);
                                {
                                    JSONObject snippet = item.getJSONObject("snippet");
                                    {
                                        titleVideo = snippet.getString("title");
                                        JSONObject thumbnails = snippet.getJSONObject("thumbnails");
                                        {
                                            JSONObject medium = thumbnails.getJSONObject("medium");
                                            {
                                                urlImage = medium.getString("url");
                                            }
                                        }
                                        JSONObject resourceId = snippet.getJSONObject("resourceId");
                                        {
                                            videoId = resourceId.getString("videoId");
                                            Toast.makeText(MainActivity.this, videoId, Toast.LENGTH_SHORT).show();
                                        }
                                    }
                                }
                            }
                        } catch (JSONException e) {
                            e.printStackTrace();
                        }
                    }
                },
                new Response.ErrorListener() {
                    @Override
                    public void onErrorResponse(VolleyError error) {
                        Toast.makeText(MainActivity.this, "Lỗi !!!", Toast.LENGTH_SHORT).show();
                    }
                });

        requestQueue.add(jsonObjectRequest);
    }
}
```

___

__HIỂN THỊ LIST VIDEO LOAD TỪ JSON__

- __ĐỐI TƯỢNG VIDEO__
- ta sẽ sử dụng ListView để hiển thị danh sách các video có trong playlist từ việc lấy JSON trả về từ url đã thiết lập trong class __Config.java__
- đầu tiên, tạo class để quản lý các đối tượng Video
- __VideoYoutube.java__
```java
public class VideoYoutube {
    private String titleVideo, thumbnailVideo, idVideo;

    public VideoYoutube(String titleVideo, String thumbnailVideo, String idVideo) {
        this.titleVideo = titleVideo;
        this.thumbnailVideo = thumbnailVideo;
        this.idVideo = idVideo;
    }

    public String getTitleVideo() {
        return titleVideo;
    }

    public void setTitleVideo(String titleVideo) {
        this.titleVideo = titleVideo;
    }

    public String getThumbnailVideo() {
        return thumbnailVideo;
    }

    public void setThumbnailVideo(String thumbnailVideo) {
        this.thumbnailVideo = thumbnailVideo;
    }

    public String getIdVideo() {
        return idVideo;
    }

    public void setIdVideo(String idVideo) {
        this.idVideo = idVideo;
    }
}
```

- __ITEM TRÊN LISTVIEW__
- thiết kế 1 file Layout để hiển thị 1 row chứa các thông tin của 1 đối tượng VideoYoutube
- __video_youtube_row.xml__
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    android:padding="5dp">

    <ImageView
        android:id="@+id/imageview_thumbnail"
        android:layout_width="120dp"
        android:layout_height="90dp"
        android:layout_margin="5dp" />

    <TextView
        android:id="@+id/textview_title"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="5dp"
        android:text="Tên Video"
        android:textColor="#1C1A1A"
        android:textSize="20sp"
        android:textStyle="bold" />

</LinearLayout>
```

- __ADAPTER__
- sau khi có class quản lý đối tượng, có layout hiển thị từng đối tượng ở từng dòng, tiến hành tạo Adapter
- __VideoYoutubeAdapter.java__ sẽ __extends BaseAdapter__
```java
public class VideoYoutubeAdapter extends BaseAdapter {

}
```

- khai báo các biến thành viên và Constructor của Adapter
```java
public class VideoYoutubeAdapter extends BaseAdapter {

    private Context context;
    private int layout;
    private List<VideoYoutube> videoYoutubeList;

    public VideoYoutubeAdapter(Context context, int layout, List<VideoYoutube> videoYoutubeList) {
        this.context = context;
        this.layout = layout;
        this.videoYoutubeList = videoYoutubeList;
    }
}
```

- khi Adapter của ta __extends BaseAdapter__ thì phải __override__ các method của __BaseAdapter__
```java
public class VideoYoutubeAdapter extends BaseAdapter {

    private Context context;
    private int layout;
    private List<VideoYoutube> videoYoutubeList;

    public VideoYoutubeAdapter(Context context, int layout, List<VideoYoutube> videoYoutubeList) {
        this.context = context;
        this.layout = layout;
        this.videoYoutubeList = videoYoutubeList;
    }

    @Override
    public int getCount() {
        return 0;
    }

    @Override
    public Object getItem(int position) {
        return null;
    }

    @Override
    public long getItemId(int position) {
        return 0;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        return null;
    }
}
```

- ở method __getCount()__ ta sửa __return__ lại như sau
```java
    @Override
    public int getCount() {
        return videoYoutubeList.size();
    }
```

- định nghĩa 1 inner class __ViewHolder__ trong Adapter có nhiệm vụ liên kết đến các thành phần trên layout __video_youtube_row.xml__
```java
    private class ViewHolder {
        ImageView imgThumbnail;
        TextView txtTitle;
    }
```

- ở method __getView()__ ta chỉnh sửa như sau
- đầu tiên khai báo đối tượng __ViewHolder__
```java
        ViewHolder holder;
```

- __getView()__ trả về 3 tham số
    - int position
    - View convertView
    - ViewGroup parent
- layout __video_youtube_row.xml__ là 1 layout do ta tự định nghĩa, nó không được quản lý bởi bất kỳ View nào, vì vậy ta cần liên kết nó với 1 View, ở đây chính là __convertView__, để __convertView__ có thể quản lý layout __video_youtube_row.xml__ ta cần thông qua __abstract class LayoutInflater__ bằng cách __inflate convertView__ bởi layout __video_youtube_row.xml__
- nhưng trên ListView sẽ có rất nhiều __convertView__, ta phải kiểm tra __convertView__ ở __position__ hiện tại đã được __inflate__ hay chưa, nếu chưa (``null``) mới tiến __inflate__ sau đó __setTag()__, nếu rồi chỉ việc __getTag()__
- sau khi đã __inflate__ ta sẽ ánh xạ __ViewHolder__ đến __layout__ của __convertView__
```java
        if (convertView == null) {
            holder = new ViewHolder();
            LayoutInflater inflater = (LayoutInflater) context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);

            convertView = inflater.inflate(layout, null);

            holder.imgThumbnail = convertView.findViewById(R.id.imageview_thumbnail);
            holder.txtTitle = convertView.findViewById(R.id.textview_title);

            convertView.setTag(holder);
        } else {
            holder = (ViewHolder) convertView.getTag();
        }
```

- khởi tạo đối tượng __VideoYoutube__ là instance của đối tượng trong __videoYoutubeList__ ở __position__ hiện tại trên __convertView__
```java
        VideoYoutube videoYoutube = videoYoutubeList.get(position);
```

- sau đó gán giá trị của đối tượng __VideoYoutube__ cho các giá trị tương ứng của đối tượng __ViewHolder__
```java
        holder.txtTitle.setText(videoYoutube.getTitleVideo());
```

- đối với __imgThumbnail__ của __ViewHolder__ là __ImageView__, nhưng của đối tượng __VideoYoutube__ lại là 1 String __url__ hình ảnh được lưu trữ trên cloud của Youtube, vì vậy để thuận tiện cho việc load hình ảnh từ __url__ về gán cho __imgThumbnail__ của __ViewHolder__ ta sử dụng library __Picasso__
- truy cập url [https://github.com/square/picasso](https://github.com/square/picasso) để thực hiện __implementation__ library này bằng cách copy paste đoạn code sau vào Gradle Module App và thực hiện Sync
```js
implementation 'com.squareup.picasso:picasso:2.8'
```

<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/51_implementation_picasso_library_for_load_image_from_url.png"> <br/>

- truy cập url [https://square.github.io/picasso/](https://square.github.io/picasso/) để xem thêm cách sử dụng library __Picasso__
- sau khi cài đặt library __Picasso__ thành công, tiến hành lấy hình ảnh từ url mà đối tượng __VideoYoutube__ cung cấp, gán vào __imgThumbnail__ của __ViewHolder__
```java
        Picasso.get().load(videoYoutube.getThumbnailVideo()).into(holder.imgThumbnail);
```

- sau cùng, __return convertView__ cho method __getView()__
```java
        return convertView;
```

- __VideoYoutubeAdapter.java__ hoàn chỉnh
```java
public class VideoYoutubeAdapter extends BaseAdapter {

    private Context context;
    private int layout;
    private List<VideoYoutube> videoYoutubeList;

    public VideoYoutubeAdapter(Context context, int layout, List<VideoYoutube> videoYoutubeList) {
        this.context = context;
        this.layout = layout;
        this.videoYoutubeList = videoYoutubeList;
    }

    @Override
    public int getCount() {
        return videoYoutubeList.size();
    }

    @Override
    public Object getItem(int position) {
        return null;
    }

    @Override
    public long getItemId(int position) {
        return 0;
    }

    private class ViewHolder {
        ImageView imgThumbnail;
        TextView txtTitle;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {

        ViewHolder holder;

        if (convertView == null) {
            holder = new ViewHolder();
            LayoutInflater inflater = (LayoutInflater) context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);

            convertView = inflater.inflate(layout, null);

            holder.imgThumbnail = convertView.findViewById(R.id.imageview_thumbnail);
            holder.txtTitle = convertView.findViewById(R.id.textview_title);

            convertView.setTag(holder);
        } else {
            holder = (ViewHolder) convertView.getTag();
        }

        VideoYoutube videoYoutube = videoYoutubeList.get(position);

        holder.txtTitle.setText(videoYoutube.getTitleVideo());
        Picasso.get().load(videoYoutube.getThumbnailVideo()).into(holder.imgThumbnail);

        return convertView;
    }
}
```

- __LISTVIEW__
- sau khi có Adapter, có class quản lý từng đối tượng trong List, layout của từng item trên ListView, ta tiến hành thiết kế 1 ListView để chứa từng layout item
- Layout của MainActivity ta đặt 1 ListView vào nó như sau
- __activity_main.xml__
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/listviewVideo"
        android:layout_width="409dp"
        android:layout_height="729dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

___

__XỬ LÝ LOGIC Ở MAIN ACTIVITY__

- đầu tiên ta khai báo và khởi tạo 3 thành phần:
    - data: là Array chứa các đối tượng Video
    - adapter: Adapter kết nối trung gian giữa data và view hiển thị
    - container: ListView sẽ hiển thị nội dung data được truyền thông qua adapter
- việc ánh xạ ListView và khởi tạo ArrayList, Adapter, sau đó thiết lập kết nối ListView và Adapter sẽ được thực hiện trong ``onCreate()``

```java
public class MainActivity extends AppCompatActivity {
    Config config;

    ListView lvVideo;
    ArrayList<VideoYoutube> arrayVideo;
    VideoYoutubeAdapter adapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        lvVideo = findViewById(R.id.listviewVideo);
        arrayVideo = new ArrayList<>();
        adapter = new VideoYoutubeAdapter(MainActivity.this, R.layout.video_youtube_row, arrayVideo);
        lvVideo.setAdapter(adapter);

        config = new Config();

        getJsonObjectYoutube(config.getPlaylistJSONObject());
    }

    //...
}
```

- phần việc khai báo biến ở đầu class, khởi tạo trong onCreate đã hoàn thành, nhưng để Array, Adapter, ListView hoạt động thì nằm ở method ``getJsonObjectYoutube``
- trong method ``getJsonObjectYoutube``, các thành phần ta cần lấy __title, thumbnail, videoId__ đều nằm trong __JSONArray items__, khi sử dụng __for-loop__ duyệt qua từng item trong JSONArray items ta sẽ có được các thành phần cần lấy, vì vậy ta sẽ chỉnh sửa __trước khi kết thúc MỘT vòng for__ và __sau khi HOÀN THÀNH TOÀN BỘ vòng for__ như sau
- trước khi kết thúc 1 vòng lặp, ta khởi tạo 1 đối tượng __VideoYoutube__ với 3 thành phần có được sau khi duyệt JSONArray items, và __add__ vào Array
- sau khi kết thúc toàn bộ vòng lặp gọi method thông báo thay đổi dữ liệu của Adapter cho ListView cập nhật lại hiển thị
- __MainActivity.java__
```java
public class MainActivity extends AppCompatActivity {
    Config config;

    ListView lvVideo;
    ArrayList<VideoYoutube> arrayVideo;
    VideoYoutubeAdapter adapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        lvVideo = findViewById(R.id.listviewVideo);
        arrayVideo = new ArrayList<>();
        adapter = new VideoYoutubeAdapter(MainActivity.this, R.layout.video_youtube_row, arrayVideo);
        lvVideo.setAdapter(adapter);

        config = new Config();

        getJsonObjectYoutube(config.getPlaylistJSONObject());
    }

    private void getJsonObjectYoutube(String urlGetJson) {
        RequestQueue requestQueue = Volley.newRequestQueue(this);

        JsonObjectRequest jsonObjectRequest = new JsonObjectRequest(
                Request.Method.GET,
                urlGetJson,
                null,
                new Response.Listener<JSONObject>() {
                    @Override
                    public void onResponse(JSONObject response) {
                        try {
                            JSONArray Items = response.getJSONArray("items");

                            String titleVideo = "", urlImage = "", videoId = "";

                            for (int i = 0; i < Items.length(); i++) {
                                JSONObject item = Items.getJSONObject(i);
                                {
                                    JSONObject snippet = item.getJSONObject("snippet");
                                    {
                                        titleVideo = snippet.getString("title");
                                        JSONObject thumbnails = snippet.getJSONObject("thumbnails");
                                        {
                                            JSONObject medium = thumbnails.getJSONObject("medium");
                                            {
                                                urlImage = medium.getString("url");
                                            }
                                        }
                                        JSONObject resourceId = snippet.getJSONObject("resourceId");
                                        {
                                            videoId = resourceId.getString("videoId");
                                        }
                                    }
                                }

                                arrayVideo.add(new VideoYoutube(titleVideo, urlImage, videoId));
                            }

                            adapter.notifyDataSetChanged();

                        } catch (JSONException e) {
                            e.printStackTrace();
                        }
                    }
                },
                new Response.ErrorListener() {
                    @Override
                    public void onErrorResponse(VolleyError error) {
                        Toast.makeText(MainActivity.this, "Lỗi !!!", Toast.LENGTH_SHORT).show();
                    }
                });

        requestQueue.add(jsonObjectRequest);
    }
}
```
<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/52_complete_listview_adapter.png"> <br/>

> Lưu ý:
>> method __getJsonObjectYoutube__ có tham số truyền vào là 1 URL dùng để lấy về 1 JSONObject, trong URL này có chứa API_KEY
>> mà việc lấy JSONObject này thông qua API Volley sử dụng giao thức HTTP để lấy JSONObject, nên nếu API_KEY có thiết lập __Application restrictions__ chỉ cho __Android apps__ thì sử dụng Volley sẽ chỉ Toast thông báo lỗi
>> nên trong cửa sổ __Key restrictions__ của __Credentials__ ở mục __Application restrictions__ trên Google Developer Console ta thay đổi thành ``None`` (không hạn chế application sử dụng KEY) và click ``SAVE``

<img src="https://github.com/hienqp/Ngay046-ConsoleCloudGoogle-PlayListYoutubeAPI/blob/main/53_volley_http_api_key.png"> <br/>

___

__PLAY VIDEO TRONG LISTVIEW__

- với việc xây dựng Adapter, ListView, đổ Data ra ListView thành công, công việc còn lại là bắt sự kiện khi user click vào 1 item (Video) bất kỳ trên ListView thì sẽ lấy ``videoId`` của item đó, Intent qua Activity khác hay Fragment để play Video đó với __id__ được truyền qua

- __XÂY DỰNG ACTIVITY PLAY VIDEO__

- tạo 1 Activity (gồm file .java và .xml) __extends YouTubeBaseActivity__ (do ở Activity này sẽ sử dụng để play video với trình phát của Youtube)
- __PlayVideoActivity.java__
```java
public class PlayVideoActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_play_video);
    }
}
```

- __BẮT LISTENER USER CLICK VÀO ITEM TRÊN LISTVIEW Ở MAIN ACTIVITY__
- để bắt sự kiện user click vào item trên ListView, trong __onCreate__ của __MainActivity__ ta sử dụng callback __setOnItemClickListener__, callback có trả về 1 vài tham số trong đó __int position__ là index của item trong mảng chứa đối tượng __VideoYoutube__
- lấy __id__ của video tại vị trí user click vào, truyền qua __PlayVideoActivity__ bằng __Intent__
```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        lvVideo = findViewById(R.id.listviewVideo);
        arrayVideo = new ArrayList<>();
        adapter = new VideoYoutubeAdapter(MainActivity.this, R.layout.video_youtube_row, arrayVideo);
        lvVideo.setAdapter(adapter);

        config = new Config();

        getJsonObjectYoutube(config.getPlaylistJSONObject());

        lvVideo.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                Intent intent = new Intent(MainActivity.this, PlayVideoActivity.class);
                intent.putExtra("idVideoYoutube", arrayVideo.get(position).getIdVideo());
                startActivity(intent);
            }
        });
    }
```

- __PLAY VIDEO ACTIVITY LẤY ID ĐƯỢC GỬI TỪ MAIN ACTIVITY THÔNG QUA INTENT__

- khởi tạo 1 empty Activity, Activity này sẽ nhận ``videoId`` truyền từ __MainActivity__ thông qua __Intent__, trước tiên ta kiểm tra ``videoId`` có được gửi qua bởi __Intent__ có thành công hay không bằng thông báo __Toast__ ở Activity nhận
- __PlayVideoActivity__
```java
public class PlayVideoActivity extends AppCompatActivity {
    String idVideo = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_play_video);

        Intent intent = getIntent();
        idVideo = intent.getStringExtra("idVideoYoutube");
        Toast.makeText(this, idVideo, Toast.LENGTH_SHORT).show();
    }
}
```

- nếu Toast thành công, ta tiến hành thiết kế layout cho __PlayVideoActivity__, vì Activity này sau khi nhận thành công ``videoId`` sẽ gọi method ``loadVideo`` để lập tức play video mà không cần đợi user click play như method ``cueVideo``, nên layout của nó chỉ đơn giản là chứa 1 view dùng để hiển thị ``YouTubePlayerView``
- __activity_play_video__
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".PlayVideoActivity">

    <view
        android:id="@+id/youtube_view"
        class="com.google.android.youtube.player.YouTubePlayerView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintBottom_toTopOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintEnd_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- quay trở lại với __PlayVideoActivity__, Activity này sẽ được __extends YouTubeBaseActivity__ và __implements YouTubePlayer.OnInitializedListener__, đồng thời khai báo ánh xạ view chứa __YoutubePlayerView__
- khi __implements YouTubePlayer.OnInitializedListener__ ta sẽ được yêu cầu phải override 2 method __onInitializationSuccess__ và __onInitializationFailure__
```java
public class PlayVideoActivity extends YouTubeBaseActivity implements YouTubePlayer.OnInitializedListener {
    YouTubePlayerView youTubePlayerView;
    String idVideo = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_play_video);

        youTubePlayerView = findViewById(R.id.youtube_view);

        Intent intent = getIntent();
        idVideo = intent.getStringExtra("idVideoYoutube");
    }

    @Override
    public void onInitializationSuccess(YouTubePlayer.Provider provider, YouTubePlayer youTubePlayer, boolean b) {

    }

    @Override
    public void onInitializationFailure(YouTubePlayer.Provider provider, YouTubeInitializationResult youTubeInitializationResult) {

    }
}
```

- sau khi ánh xạ được __YoutubePlayerView__, ta cho đối tượng __youtubePlayerView__ gọi method __initialize(String, Context)__ để khởi tạo trình phát video Youtube, trong đó 2 tham số cần truyền vào là __YOUTUBE_API_KEY__ và __Context__ (PlayVideoActivity đã implement YouTubePlayer.OnInitializedListener)
- để cho thuận tiện việc khởi tạo lại khi thất bại ta nên tạo 1 method riêng chứa lệnh gọi __initialize()__ trong PlayVideoActivity
```java
    private void initYoutubeConnection() {
        youTubePlayerView.initialize(MainActivity.config.getYOUTUBE_API_KEY(), PlayVideoActivity.this);
    }
```
> vì đối tượng __Config__ dùng để gọi __YOUTUBE_API_KEY__ đã được ta tạo ở MainActivity, để có thể gọi đối tượng này ở PlayVideoActivity, thì ở MainActivity ta khai báo thêm modifier cho đối tượng này là ``public static Config config;``

- trong __onCreate__ của PlayVideoActivity ta chỉ việc gọi method đã xây dựng __initYoutubeConnection__
```java
public class PlayVideoActivity extends YouTubeBaseActivity implements YouTubePlayer.OnInitializedListener {
    YouTubePlayerView youTubePlayerView;
    String idVideo = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_play_video);

        youTubePlayerView = findViewById(R.id.youtube_view);

        Intent intent = getIntent();
        idVideo = intent.getStringExtra("idVideoYoutube");

        initYoutubeConnection();
    }

    @Override
    public void onInitializationSuccess(YouTubePlayer.Provider provider, YouTubePlayer youTubePlayer, boolean b) {
        
    }

    @Override
    public void onInitializationFailure(YouTubePlayer.Provider provider, YouTubeInitializationResult youTubeInitializationResult) {
        
    }

    private void initYoutubeConnection() {
        youTubePlayerView.initialize(MainActivity.config.getYOUTUBE_API_KEY(), PlayVideoActivity.this);
    }
}
```

- 2 method ta đã override là 2 callback dùng để lắng nghe việc khởi tạo thành công hay thất bại
- nếu thành công thì ở __onInitializationSuccess__ ta chỉ việc lấy đối tượng __YoutubePlayer__ trả về method gọi method __loadVideo()__ với tham số truyền vào là ID của video nhận được bởi Intent
```java
    @Override
    public void onInitializationSuccess(YouTubePlayer.Provider provider, YouTubePlayer youTubePlayer, boolean b) {
        youTubePlayer.loadVideo(idVideo);
    }
```

- nếu __initialize()__ thất bại, callback __onInitializationFailure()__ sẽ được gọi, trong callback này trả về đối tượng là kết quả của việc khởi tạo thất bại __youTubeInitializationResult__, ta sẽ sử dụng đối tượng này để kiểm tra việc khởi tạo thất bại có phải từ phía user hay không
    - nếu là lỗi từ user, từ đối tượng __youTubeInitializationResult__ ta gọi hiển thị Error Dialog, với 2 tham số truyền vào cho nó là
        - Context
        - số kiểu ``int`` (là 1 REQUEST_CODE, giá trị này sẽ được gửi đi để thử khởi tạo lại lần nữa, và dùng để kiểm tra kết quả trả về)
    - nếu không phải lỗi từ user, ta có thể xử lý đơn giản là Toast thông báo cho user

- ta sẽ khai báo 1 REQUEST_VIDEO kiểu ``int``
```java
public class PlayVideoActivity extends YouTubeBaseActivity implements YouTubePlayer.OnInitializedListener {
    YouTubePlayerView youTubePlayerView;
    String idVideo = "";
    int REQUEST_VIDEO = 123;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_play_video);

        youTubePlayerView = findViewById(R.id.youtube_view);

        Intent intent = getIntent();
        idVideo = intent.getStringExtra("idVideoYoutube");

        initYoutubeConnection();
    }

    @Override
    public void onInitializationSuccess(YouTubePlayer.Provider provider, YouTubePlayer youTubePlayer, boolean b) {
        youTubePlayer.loadVideo(idVideo);
    }

    @Override
    public void onInitializationFailure(YouTubePlayer.Provider provider, YouTubeInitializationResult youTubeInitializationResult) {
        if (youTubeInitializationResult.isUserRecoverableError()) {
            youTubeInitializationResult.getErrorDialog(PlayVideoActivity.this, REQUEST_VIDEO);
        } else {
            Toast.makeText(this, "Lỗi không load được Video", Toast.LENGTH_SHORT).show();
        }
    }

    private void initYoutubeConnection() {
        youTubePlayerView.initialize(MainActivity.config.getYOUTUBE_API_KEY(), PlayVideoActivity.this);
    }
}
```

- với REQUEST_VIDEO gửi đi được dùng để thử khởi tạo lại, ta sẽ gọi callback ``onActivityResult()`` để lấy kết quả trả về, nếu __requestCode__ trả về trùng với __REQUEST_VIDEO__ ta sẽ khởi tạo lại lần nữa việc kết nối đến Youtube
```java
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == REQUEST_VIDEO) {
            initYoutubeConnection();
        }
        super.onActivityResult(requestCode, resultCode, data);
    }
```

- run app để kiểm tra

> Lưu ý: ở máy ảo để có thể sử dụng các dịch vụ của Google (ví dụ ở đây là YoutubePlayerView và khởi tạo kết nối API Youtube Data V3), thì máy ảo đó cần cài đặt Google Play Service

___

__XỬ LÝ VÀI THAO TÁC VỚI GIAO DIỆN YOUTUBE PLAYER VIEW__

- giả sử khi chuyển qua Activity chứa YoutubePlayerView, ta đã thiết lập view tự động play video, nhưng ta muốn Player tự động xoay ngang để khung video được hiển thị lớn nhất
- để set full screen cho YoutubePlayerView, thì sau khi khởi tạo thành công (``onInitializationSuccess``) và load được ``videoId`` ta gọi method ``setFullscreen(boolean)``
```java
    @Override
    public void onInitializationSuccess(YouTubePlayer.Provider provider, YouTubePlayer youTubePlayer, boolean b) {
        youTubePlayer.loadVideo(idVideo);
        youTubePlayer.setFullscreen(true);
    }
```

- với việc gọi method ``setFullscreen()`` như trên vẫn có thể xảy ra tình trạng giật lag khi chuyển màn hình, và khi di chuyển qua lại giữa 2 màn hình thì video sẽ load lại video từ đầu, để giải quyết ta sẽ can thiệp vào thuộc tính của 2 Activity trong __AndroidManifest__
- mở file AndroidManifest.xml ta thêm thuộc tính ``android:screenOrientation="landscape"`` cho thẻ __PlayVideoActivity__
```xml
        <activity
            android:name=".PlayVideoActivity"
            android:exported="false"
            android:screenOrientation="landscape">
            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
```
- ở thẻ __MainActivity__ ta thêm thuộc tính sau ``android:configChanges="orientation|screenSize"`` để giải quyết tình trạng load lại từ đầu video
```xml
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:configChanges="orientation|screenSize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
```

___