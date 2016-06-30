# ffmpeg
ffmpeg 安装，转视频格式为m3u8，压缩视频

## ffmpeg 安装
直接安装：

    apt-get install ffmpeg
  
运行 `ffmpeg` 看是否出现版本号以判断是否安装成功

如果不成功运行full-ffmpeg.sh 

    ./full-ffmpeg.sh

## ffmpeg转视频格式为m3u8

    ffmpeg -i test.mp4 -codec:v libx264 -codec:a mp3 -map 0 -f ssegment -segment_format mpegts -segment_list playlist.m3u8 -segment_time 10 out%03d.ts

-i : 引入视频源
-codec:v : 视频格式
-codec:a : 音频格式
segment_format: 来指定输出格式为mpegts   
segment_list: 用来配置输出的列表文件名
segment_time: 切片的时长
详见：<https://www.ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment/>

## ffmpeg压缩视频

    ffmpeg -i test.mp4 -vcodec libx264 -preset fast -crf 24 -y -vf "scale=1920:-1" -acodec libmp3lame -ab 128k 12.min.mp4

详见：<https://segmentfault.com/a/1190000002502526/>


#### 参考：
<http://elkpi.com/topics/ffmpeg-f-hls.html/> <br>
<http://www.cnblogs.com/top5/archive/2009/12/30/1636352.html/>
