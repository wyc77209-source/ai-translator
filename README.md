# AI 同声翻译 · Live Translator（MVP）

在线地址：https://wyc77209-source.github.io/ai-translator/

中↔英双向实时对话翻译。纯静态网页，无后端、无密钥入库。

## 怎么用
1. 你用手机打开网页（Chrome / Safari），默认「我说中文」。
2. 对方用手机扫二维码，浏览器直接打开，无需安装，默认「I speak EN」。
3. 双方各自点麦克风说话：
   - 说话过程中的**预测/中间结果只上字幕**（虚线气泡）；
   - 句子确认后才翻译定稿，并在**对方手机上用 TTS 朗读**（猜测只上字幕，不上耳朵）。
4. 没人扫码时是单机模式：译文在本机朗读。

## 技术
- 语音识别 / 朗读：浏览器 Web Speech API（SpeechRecognition + speechSynthesis）。
- 翻译：⚙︎ 设置里填你自己的 OpenAI Key（只存在本机 localStorage，用 gpt-4o-mini）→ 否则免费 Google 网页翻译接口 → 再否则 MyMemory。
- 双端同步：优先 WebRTC（PeerJS 公共信令）；连不上时自动走 ntfy.sh 公共中继（随机房间名；中间结果限流 1.5 秒一条）。

## 已知限制
- 语音识别需 Chrome（安卓/桌面）或 iOS Safari 14.5+；Firefox 不支持。
- 免费翻译接口不保证稳定，有限流；正式用建议填 Key。
- ntfy.sh 中继是公开服务，房间名随机但不加密，不要谈机密内容。
