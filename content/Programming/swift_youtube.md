Title: Youtubeの動画URLを取得して再生するSwiftコードを書いた
Date: 2013-06-19 08:28:30
Tags: Swift

Objective-Cだと以下のプロジェクトで、YoutubeからiOSで再生可能な形式の動画を取得して再生している。その中身を明らかにして、Swiftで書き直す話。

[hellozimi/HCYoutubeParser](https://github.com/hellozimi/HCYoutubeParser "hellozimi/HCYoutubeParser")

```
http://www.youtube.com/get_video_info?video_id=<video_id>
```

で取得できるデータから引っ張り出すことができる。

データがURLのQuery形式になっていて、そのパーサが必要。

動画データは、url_encoded_fmt_stream_mapに入っている。

# GET

非同期でGETする。

```swift
let url = "http://www.youtube.com/get_video_info?video_id=<ID>"
var req = NSMutableURLRequest(URL: NSURL(string: url)!)
req.HTTPMethod = "GET"
var task = NSURLSession.sharedSession().dataTaskWithRequest(req, completionHandler: {data, response, error in
    if (error == nil) {
        var result = NSString(data: data, encoding: NSUTF8StringEncoding)!
        println(result)
    } else {
        println(error)
    }
})
task.resume()
```

# GETしたレスポンスをパース

URLクエリ文字列をパースしてDictionaryに入れる。パースしたあとのデータはstringByRemovingPercentEncodingでデコードする必要があるので注意。

```swift
var parameters: Dictionary = [String: String]()
for key_val in split(str, { $0 == "&" }) {
    let key_val_array = split(key_val, { $0 == "=" })
    //println(key_val_array)
    let key = key_val_array[0]
    let val = key_val_array[1].stringByRemovingPercentEncoding
    parameters[key] = val;
}
return parameters
```

# 必要そうなデータ

thumbnail_url, length_seconds, iurl, title, iurlmq, url_encoded_fmt_stream_map, iurlmaxres, iv_module(swfのリンクになってる、つかえるのかな？), vid, iurlsd
