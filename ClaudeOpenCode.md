```
.claude/
├── settings.json
├── settings.local.json
├── CLAUDE.md
├── CLAUDE.local.md
├── agents/
├── skills/
├── rules/
│   ├── code-style.md
│   └── frontend/react.md
└── .mcp.json

$ tree .opencode
.opencode
├── bin/opencode
├── bun.lock
├── node_modules
│   ├── @opencode-ai
│   └── zod
└── package.json

$ cat .config/opencode/opencode.json
{
  "plugin": [
    "oh-my-opencode"
  ],
  "$schema": "https://opencode.ai/config.json"
}
```

# Speech vs Text

[Google Cloud Text-to-Speech](https://docs.cloud.google.com/text-to-speech/docs/create-audio): Speech Synthesis Markup Language (SSML)
```
<say-as interpret-as="characters">SSML</say-as>
```

方法一：直接驅動 FFmpeg（適合基礎剪輯、轉檔與畫面處理）

適用場景： 影片裁切、加速、合併、加浮水印、壓製字幕。

實作方式： FFmpeg 是強大但語法極度複雜的工具，現在只需在 Claude Code 中用白話文下令。例如輸入：「把 input.mp4 影片開頭的黑畫面剪掉，畫面裁切成適合 Instagram 的正方形，整體速度調快兩倍，並在右下角加上 QR Code 浮水印」 。

結果： Claude 會自動為你寫出精確的 FFmpeg 終端機指令、自動執行，並驗證最終輸出的檔案是否成功 。

方法二：結合 Remotion 框架（適合製作行銷短影音、動態文字與圖表）

適用場景： 需要精緻文字動畫、社群媒體宣傳片、SaaS 產品展示介面模擬。

實作方式：

在終端機輸入 npx create-video@latest 初始化一個乾淨的專案 。

輸入 npx skills add remotion-dev/skills 安裝官方技能，這能讓 Claude 瞬間掌握製作動畫的最佳邏輯 。

向 Claude 許願：「做一個 30 秒的產品宣傳影片，畫面要有粗體文字飛入的動畫，搭配平滑轉場與藍色漸層背景」 。

執行 npm run dev，就能在瀏覽器即時預覽 Claude 寫好的影片，不滿意可隨時叫它修改 。

方法三：搭配 MoviePy MCP 伺服器（適合需要進階邏輯與防呆處理）

適用場景： 複雜濾鏡、多軌道串接、時間軸操作。

實作方式： 透過安裝 MoviePy MCP 伺服器並整合進配置檔後，可以讓 Claude 執行更連貫的操作 。例如輸入：「載入這段影片，將解析度縮小為 720p，全片套用黑白濾鏡，並在影片最後兩秒加入聲音與畫面的淡出效果」。Claude 會在記憶體內追蹤這些影片片段（Clip），並有效率地一次性渲染出結果，避免產生大量暫存檔 。

方法四：生成 EDL 腳本（適合長篇訪談或 YouTube 粗剪）

適用場景： 快速剔除影片中的冗言贅字或長時間的無聲空白。

實作方式： 不要讓 AI 直接去剪超大檔案的影片（會非常耗時）。可以先把影片的「逐字稿（Transcript）」提供給 Claude，篩選精華重點，或是請它寫腳本抓出超過 1.5 秒的靜音片段 。接著，要求 Claude 輸出一份 .edl（Edit Decision List）純文字檔 。最後，只需將這個 .edl 檔直接拖入 DaVinci Resolve 等專業剪輯軟體，所有剪輯切點就會瞬間自動完成，大幅省去人工手動裁切的時間 。

如果想要生成影片，可以使用vpick 自動生圖 ，再圖生影片，甚至是串接聲音配音，把 kling , nanobanana等一次完成

