# フィジカルAI時代の自作DIYプロジェクト完全ガイド

**SISYPHUS砂テーブルから完全ローカルAIアシスタントまで、ソフトウェアとハードウェアが交差する60以上のDIYプロジェクト**を、6つのカテゴリで整理した。注目すべきは、2025〜2026年にかけてエッジAIが急速に民主化した点だ。Hailo AI HAT+（26 TOPS）が$70で手に入り、Hugging FaceのLeRobot/Reachy Miniがロボット工学を$100台に引き下げ、Home Assistant Voice PE（$59）が完全ローカル音声アシスタントを「買える前提」に変えた。ESPHome 2025.6ではESP32-C6/H2のOpenThreadがネイティブ対応し、Matter/Thread自作デバイスもYAML数十行で書ける時代になった。砂テーブルのZenXY、Sisbotは成熟しSandifyだけでパターン生成が完結する。ニキシー管時計のような「見た目の美学」プロジェクトも依然強い。以下、カテゴリ別に具体的プロジェクトを整理する。

---

## 砂・ペン・光で描くキネティックアート

SISYPHUSの枯山水テーブルに最も近い体験を得るなら、**ZenXY v2**（V1 Engineering）が王道だ。CoreXYベルトで磁石を動かし、砂中の鉄球で幾何模様を描く。TMC2209ドライバと重曹を使えば**ほぼ無音で動作**し、成熟したエコシステム（Sandifyでパターン生成、GRBL互換、Sisyphus公式`.thr`ファイルも再生可）がある。ガラス天板のある既存テーブルをドナーにすれば木工工数も削減できる。同じステッパー知識はそのままAxiDraw型ペンプロッターへ応用可能で、「砂→紙」の発展コースが自然に描ける。

| プロジェクト | ハード／ソフト | 難易度 | 予算 | 参考 |
|---|---|---|---|---|
| **ZenXY v2 砂テーブル** | NEMA17×2、TMC2209、ESP32 Grbl、3Dプリント部品／Sandify＋GRBL | 中級 | $300〜600 | docs.v1e.com/zenxy、sandify.org |
| **CoreXY Sand Table（rdudhagra版）** | OpenBuilds V-Slot、Pi内蔵WebUI／Sisyphus `.thr`互換 | 中〜上級 | 〜$750 | github.com/rdudhagra/Sand-Table |
| **AxiDrawクローン（4xiDraw / Blot）** | NEMA17×2、SG90サーボ、CNCシールド／saxi・axi・vpype・Inkscape | 中級 | $100〜250 | github.com/beardicus/awesome-plotters |
| **Split-Flap ディスプレイ（Scott Bezek版）** | 28BYJ-48、ESP32 Chainlink、PVCフラップ／PlatformIO＋WebUI | 中〜上級 | 1モジュール$30〜50 | github.com/scottbez1/splitflap |
| **ハーモノグラフ（3振り子）** | 木材＋振り子錘、ユニバーサルジョイント／電子制御なし（純機械） | 初〜中級 | $30〜100 | karlsims.com/harmonograph |
| **自動ストリングアート機（StringIT!）** | NEMA23、MG996Rサーボ×2、ESP32／Pythonグリーディ＋wowstrings.com | 上級 | $200〜500 | instructables.com/StringIT |
| **POVディスプレイ** | ESP32＋WS2812B 128個、ホールセンサ同期、スリップリング | 初〜上級 | $20〜100 | circuitdigest.com POV ESP32 |
| **3Dプリント フリップクロック** | 28BYJ-48×3、ESP32 NTP／Python or Arduino | 初〜中級 | $50〜150 | printables.com/model/18076 |
| **CNC×ライトペインティング** | 既存3Dプリンタ＋WS2812B LED／Blender＋Pythonで各フレームG-code | 中級 | 既存+$20〜50 | hackaday.com 2018/07/30 Josh Sheldon |

---

## Raspberry Pi / Arduino / ESP32で作るインテリアオブジェ

「毎日使いたい×見た目が映える」ラインでは、**MagicMirror²**がMagPi読者投票1位の地位を守り続けている。マジックミラーアクリルの裏にモニターを置き、時刻・天気・カレンダー・Spotify再生情報を反射越しに表示する。玄関や洗面所で毎朝使える実用性と、モジュラー設計の拡張性が魅力。もう一つの定番は**E-Paper天気ダッシュボード**で、FireBeetle ESP32-E＋7.5インチWaveshareの組み合わせは5000mAhバッテリーで6ヶ月以上動作する超低消費電力設計。IKEAのRIBBAフレームに入れて「動く写真立て」にする構成がHome Assistantコミュニティでほぼ標準化している。

| プロジェクト | ハード／ソフト | 難易度 | 予算 |
|---|---|---|---|
| **MagicMirror²** | Pi 4＋HDMIモニター＋マジックミラーアクリル／Electron＋Node.js | 中級 | 1.5〜3万円 |
| **ESP32 E-Paper 天気ダッシュボード** | FireBeetle ESP32-E＋Waveshare 7.5"／GxEPD2＋OpenWeatherMap | 中級 | 1.2〜2万円 |
| **HUB75 ピクセルアート ディスプレイ** | ESP32-S3＋64×64 HUB75／WLED、Pixelix、PixelIt | 中級 | 0.8〜1.5万円 |
| **Word Clock** | Arduino Nano ESP32＋WS2812B×114／FastLED＋NTP | 中級 | 0.8〜1.5万円 |
| **天気クラウドランプ** | Pi Zero 2 W＋WS2812B、綿ディフューザ／OpenWeatherMap API | 初〜中級 | 0.4〜1万円 |
| **インフィニティミラー時計** | WS2812B 60〜120個、ハーフミラー＋通常ミラー／BiblioPixel | 中級 | 0.8〜2万円 |
| **Pi-hole カスタム筐体版** | Pi Zero 2 W＋Ethernet HAT、OLEDステータス／Pi-hole＋Unbound | 初級 | 0.5〜1.2万円 |
| **RetroPie ミニアーケード** | Pi 4＋Sanwaボタン＋17"LCD＋MDF筐体／RetroPie | 中〜上級 | 1.5〜5万円 |
| **招き猫 Slack Notifier** | ESP32＋サーボ改造招き猫／Slack Events API | 初級 | 0.2〜0.7万円 |

---

## 完全ローカル・プライベートなスマートホーム

2026年のDIYスマートホームは、**Home Assistant OS + ESPHome + Matter/Thread**という新三層構造が決定版になった。ESPHome 2025.6.0でESP32-C6/H2のOpenThreadがYAMLだけで書けるようになり、Wi-Fi不要の低消費電力IoTデバイスを$10前後で作れる。mmWaveセンサー**HLK-LD2410**（約$15）はPIRと違い「静止した在室」を検知でき、Aqara FP2（$167）の90%オフで同等機能を実現する。音声系では**Home Assistant Voice PE**（$59、Nabu Casa公式）が登場し、WillowやRhasspyなど従来の選択肢は役割を終えつつある。ただし完全ローカルLLM対話（Ollama + Llama 3.2 + Whisper + Piper）をHAに統合するのは依然として最も創造的な構築プロジェクトだ。

Philips Hueの代替は**WLED + diyHue**の組み合わせで完結する。diyHueはRaspberry Pi上でHue Bridgeをエミュレートするため、Hue公式アプリやHue Syncからそのまま操作できる。カーテン自動化はSwitchBotカーテン（市販$99）の代わりに**ESP32 + NEMA17 + TMC2209**を3,000〜6,000円/窓で構築可能。Apple HomeKey対応のスマートロックすら、**HomeKey-ESP32**プロジェクトで$150以下で既存デッドボルトに後付けできる時代になった。

| プロジェクト | 主要技術 | 難易度 | 予算 |
|---|---|---|---|
| **HA + ESPHome基盤** | Pi 4/5＋HA OS＋Mosquitto MQTT | 初〜中級 | 1〜2万円 |
| **自作スマートカーテン** | ESP32＋NEMA17＋TMC2209／ESPHome cover | 中級 | 3,000〜6,000円/窓 |
| **壁スイッチ裏Shelly1化** | Shelly1 + ESPHome書換／物理フェイルオーバー可 | 中級 | 1,500〜4,000円/箇所 |
| **ESP-360-REMOTE IRハブ** | ESP32＋IR全方位＋RF 433MHz＋温湿度／SmartIR | 中級 | 500〜2,000円 |
| **mmWave在室センサー** | ESP32-C3＋HLK-LD2410／ESPHome ld2410 | 初級 | 1,500〜2,500円 |
| **自作スマートロック** | ESP32＋NEMA23＋指紋R503／HomeKey-ESP32でApple Home対応 | 上級 | 3,000〜8,000円 |
| **E-Paperダッシュボード** | LILYGO T5 4.7" or Waveshare 7.5"／ESPHome LVGL | 中級 | 5,000〜10,000円 |
| **HA Voice PE + Ollama** | Voice PE $59＋miniPC／HA Assist＋Llama 3.2＋Whisper | 中〜上級 | 1〜3万円 |
| **Matter/Thread自作デバイス** | ESP32-C6/H2／ESPHome OpenThread | 中級 | 約800円〜 |

**注意点**: AC100Vを扱う配線はShellyなど認証済みモジュールをベースにすること。Willowは2025年後半から更新頻度が低下しており、新規採用はHA Assist系を推奨する。

---

## 物理ボタン、ダイヤル、ジェスチャーで繋ぐ世界

ユーザーが例示した「WoL代替の物理電源ボタン」は、**ESPHome PC Power Control**が最短解だ。ESP8266をマザーボードのF_PANEL端子にフォトカプラ経由で繋ぎ、HAから`switch.turn_on`を叩けば物理ボタン押下をエミュレートする。電源LEDのステータスも読み取れ、WoL不要・起動不能時の強制電源断も可能。

もう一つの白眉が**SmartKnob View**（Scott Bezek作）。BLDCジンバルモーターをFOCクローズドループ制御し、**ソフトウェアで仮想デテント（カチッ感）やエンドストップを定義**できるダイヤル。240×240丸型LCDを内蔵し、「今はボリュームノブ」「次はエアコン温度」と動的にハプティックを変えられる。SparkFunが組立済みMaTouch SmartKnob（$69）も販売中。簡易版なら**M5Stack Dial**が既製ハードで$30、ESPHomeを焼けば即HA統合できる。

| プロジェクト | ハード／ソフト | 難易度 | 予算 |
|---|---|---|---|
| **ESP32物理電源ボタン** | ESP8266＋PC817フォトカプラ／ESPHome＋HA | 初級 | $5〜15 |
| **Adafruit MacroPad RP2040** | RP2040＋Cherry MX×12＋OLED／QMK or CircuitPython | 初級 | $40〜60 |
| **Big Red Buttonマクロ** | Pico＋60mmアーケードボタン／CircuitPython HID | 初級 | $10〜20 |
| **SmartKnob View** | ESP32＋BLDC＋MT6701＋GC9A01 LCD／SimpleFOC | 上級 | $60〜120 |
| **M5Stack Dial** | M5StampS3内蔵／ESPHome | 初級 | $30〜40 |
| **deej 物理音量ミキサー** | Arduino Nano＋スライダー×5／Goクライアント | 初級 | $15〜25 |
| **USBフットペダル** | Arduino Leonardo＋サステインペダル／HID Keyboard | 初級 | $15〜30 |
| **MPR121タッチアート** | Adafruit MPR121＋導電素材／I²C×4で48ch拡張可 | 初〜中級 | $10〜25 |
| **PAJ7620ジェスチャー** | GY-PAJ7620＋Arduino／9種類のジェスチャーI²C出力 | 初級 | $5〜15 |
| **MediaPipe Handsカメラ制御** | PCのWebカメラのみ／Python＋OpenCV＋PyAutoGUI | 中級 | $0 |
| **ESP32 BLE HIDボタン** | M5StampC3U＋タクトスイッチ／ESP32-BLE-Keyboard | 初〜中級 | $5〜15 |
| **ESP32 e-Paperポモドーロ** | ESP32-S3＋Waveshare 4.26"＋エンコーダ／LVGL | 中級 | $30〜50 |

---

## フィジカルAI――エッジで動くローカル知能

このカテゴリが2025〜2026年で最も劇的に変化した。**Hailo AI HAT+ (26 TOPS) とRaspberry Pi 5の組み合わせ**により、Gemma 3やLlama 3.2を**完全オフラインで動かす$200台のLLMサーバー**を自作できるようになった。hailo-ollamaはOllama互換APIを提供し、OpenWebUIで普通のChatGPT風UIを使える。NVIDIA Jetson Orin Nano Superは2024年末の値下げ（$499→$249）とソフトウェア更新で67 INT8 TOPSに達し、ビジョンAIエージェントやAI双眼鏡（Swarovski AX Vision $4,799の代替）の現実的なプラットフォームになった。

もうひとつの革命は**Hugging FaceのLeRobot/Reachy Mini**だ。SO-ARM101は$100〜の3Dプリント製デュアルロボットアームで、模倣学習と強化学習に対応、Hugging Face Hubで学習済みポリシーを共有できる。Reachy Mini（$299〜$449）は卓上ヒューマノイドとして出荷され、Hugging Face Spacesで「アプリ」を配布するロボットOS型エコシステムを標榜する。小型VLMも爆発的に拡充された――**Moondream 2B**をPi 5で動かせば「洗濯物は干してある？」「玄関に荷物ある？」といった自然言語クエリに画像応答できる（応答8〜25秒）。Phi-3 mini、Llama 3.2 1B/3B、Gemma 3 270mなどRaspberry Piクラスで動くモデルが爆増している。

| プロジェクト | 主要技術 | 難易度 | 予算 |
|---|---|---|---|
| **Pi 5 + Hailo AI HAT+ LLMサーバー** | Pi 5 16GB＋Hailo-10 26 TOPS／hailo-ollama＋Gemma3 | 中級 | $150〜250 |
| **HA Voice PE + ローカルLLM** | Voice PE＋Pi5／HA Assist＋Ollama＋Whisper＋Piper | 初〜中級 | $60〜300 |
| **Moondream VLMカメラ** | Pi 5 16GB＋Pi Camera v3／Moondream 2B＋PiCamera2 | 初〜中級 | $120〜150 |
| **LeRobot SO-ARM101** | Feetech ST3215×12＋Pi5 or Jetson Orin NX／PyTorch＋ACT/Diffusion Policy | 中〜上級 | $250〜500 |
| **Reachy Mini（HF公式）** | 6DOFヘッド＋広角カメラ＋4マイク／Python SDK＋HF Hub | 中級 | $299〜449 |
| **XIAO ESP32-S3 Sense TinyML** | OV2640＋デジタルマイク／Edge Impulse＋SenseCraft AI＋Plumerai | 初〜中級 | $15〜40 |
| **AI Pendant（Omi/Friend）** | nRF52＋MEMSマイク＋ボタン電池／Whisper＋Ollama＋Pinecone | 中〜上級 | $30〜99 |
| **Jetson Orin Nano Super 鳥認識双眼鏡** | Jetson Orin Nano Super＋双眼鏡マウント／YOLO11＋BirdNET | 中〜上級 | $280〜400 |
| **Willow音声アシスタント** | ESP32-S3-BOX-3＋Willow Inference Server／500ms応答 | 初〜中級 | $50〜150 |
| **AIテディベア（Ted）** | ESP32 or Pi 4＋MAX98357 I2S／Whisper＋ChatGPT or Ollama＋Piper | 中級 | $80〜150 |

**注目トレンド**: Frigate NVR v0.16はCoral TPU上で物体検出＋顔認識＋ナンバー認識を完全ローカルで実現。Looking Glass（$99〜）を使ったAIホログラムアバターや、ESP32-S3-BOX-3を核にしたオンデバイスwake word（microWakeWord）が低消費電力デバイスに浸透している。

---

## ニキシー管とフリップドット――レトロ美学の復権

インテリア価値で頂点に立つのが**IN-18 ESP32ニキシー管時計**だ。オレンジ色の放電グローは他に代替がなく、NTP同期・WebUI設定・バッテリーバックアップまで現代化された設計が公開されている。ただしIN-18は$45〜$70/本と高騰しており、6桁構成で5万円を超える。新品製造は停止済みでAliExpressやgra-afch.com（ウクライナ）からのNOSが頼り。偽リマーク品もあるためテスト済み出品者を選ぶこと。**170Vを扱うため安全対策は必須**（絶縁距離5mm、GND接地、電源断後のコンデンサ放電待ち）。

「ニキシー欲しいけど高電圧が怖い・予算厳しい」なら**Lixie II**が解答だ。レーザーカットアクリル板の縁に数字を彫刻しWS2812Bでエッジライトする構造で、高電圧不要・フルカラー・1桁$32から。**VFD（IV-18 蛍光表示管）**は50Vと中間電圧でニキシーより安全、青緑色の柔らかな発光が魅力で日本のAkafuguがキット販売している。

派手さ重視なら**Alfa-Zetaフリップドットパネル**。電磁機械で黄/黒円盤を物理反転させる「カチカチ」音が唯一無二で、電源OFFでも表示保持される。28×7パネルで$200〜$500、RS-485プロトコルでArduino/ESP32から制御可能。Bezek氏の**Split-Flapディスプレイ**はより静かな発車標風表現で、10年以上メンテされている最も成熟した設計。

| プロジェクト | ハード／ソフト | 難易度 | 予算 |
|---|---|---|---|
| **ESP32 IN-14/IN-18ニキシー時計** | IN-14×4〜6、K155ID1、NCH6100HV昇圧／Arduino＋NTP | 中〜上級 | 2〜5万円 |
| **Lixie II（ニキシー代替）** | WS2812B×22/桁、レーザー彫刻アクリル／Lixie II Lib | 初級 | 1〜2万円 |
| **IV-18 VFD時計** | IV-18＋MAX6921、ATmega328P／Arduino＋NTP | 中級 | 1.5〜3万円 |
| **Alfa-Zetaフリップドット** | 28×7パネル＋RS-485＋24V／Arduino serial protocol | 中級 | 3〜8万円 |
| **Split-Flap（Scott Bezek）** | 28BYJ-48、ESP32、3Dプリント／PlatformIO＋WebUI | 中〜上級 | 1モジュール3,000円 |
| **Word Clock** | WS2812B×110、ESP8266／techniccontroller firm | 初〜中級 | 1〜1.5万円 |
| **Retro Lite CM4（携帯機）** | Pi CM4＋5.5"IPS＋4000mAh LiPo＋CNCアルミ／Batocera | 上級 | 3〜8万円 |
| **ヴィンテージラジオSpotify化** | Pi Zero W＋MAX98357A／Mopidy＋Spotifyプラグイン | 初〜中級 | 8,000〜15,000円 |
| **Pi Zero サーマルポラロイド** | Pi Zero＋Piカメラ＋Nano Thermal Printer／Pythonディザ処理＋（任意）LLaVA字幕 | 中級 | 1〜2万円 |
| **RC2014 / Gigatron / Ben Eater 8bit** | Z80 or 74xxTTLロジック／Microsoft BASIC | 初〜上級 | $40〜$300 |
| **Mini Macintosh（3Dプリント）** | Pi Zero 2 W＋3.5" LCD＋原寸40%筐体／Mini vMac＋System 7 | 中級 | 〜1万円 |
| **サイバーデック（Cyberdeck）** | Pi 400 or CM4＋小型LCD＋メカキーボード＋Pelicanケース | 中〜上級 | 2〜6万円 |

---

## 結論――入門ロードマップと次の一手

**「SISYPHUSの体験に最も近い初手」はZenXY v2**で、Sandifyエコシステムが極めて成熟しておりSlack的な参入障壁の低さがある。そこから紙面描画に興味が移れば同じGRBL/ステッパー知識でAxiDraxクローンに直行でき、表示系に関心が広がればSplit-Flapが自然な次のステップだ。スマートホームを始めるなら**Home Assistant OS + ESPHome + ESP32-C6（OpenThread）**が2026年時点の決定版で、Matter/Thread対応機を$10で作れる時代は数年前には想像できなかった。

**AI×ハードウェアで2026年に試すべきは3つ**――(1) Hailo AI HAT+でPi 5をLLMサーバー化、(2) Home Assistant Voice PE + Ollamaで家庭内Alexaを完全ローカル化、(3) LeRobot SO-ARM101で模倣学習ロボット入門。いずれも$60〜$500の範囲で、1年前はクラウドAPI経由でしかできなかった体験がオンデバイスで動く。重要な変化は「フィジカルAI」が**研究室の言葉から週末DIYの語彙になった**ことだ。

予算10,000円以下で始めるなら**ESP32物理電源ボタン（$10）→ deej音量ミキサー（$20）→ Pi-hole筐体版（5,000円）→ Word Clock（1万円）**の順が学習コストと満足度のバランスが良い。見た目の完成度で選ぶなら**Word Clock、Split-Flap、IN-18ニキシー時計、ヴィンテージラジオSpotify化**の4つがユーザーのインテリア志向に最もマッチする。

---

## 参照

### キネティックアート・砂テーブル
- ZenXY v2 Sand Table — https://www.v1e.com/blogs/news/zenxy-v2-sand-table
- Hackaday: Kinetic Sculpture — https://hackaday.com/tag/kinetic-sculpture/
- Sandify（パターン生成） — https://sandify.org/
- Scott Bezek Split-Flap Display — https://github.com/scottbez1/splitflap
- Awesome Plotters — https://github.com/beardicus/awesome-plotters

### インテリアオブジェ
- MagicMirror² — https://magicmirror.builders/
- Raspberry Pi: How to Build a Smart Mirror — https://www.raspberrypi.com/tutorials/how-to-build-a-super-slim-smart-mirror/
- MagicMirror: My First Ever Raspberry Pi Project (Medium) — https://medium.com/@stacha.l/magic-mirror-my-first-ever-raspberry-pi-project-ced7985ff1a
- ESP32 E-Paper Weather Display — https://hackaday.io/project/189708-esp32-e-paper-weather-display
- Infinity Mirror Clock — https://hackaday.io/project/1852-infinity-mirror-clock
- Maniacal Labs: Infinity Mirror — https://maniacallabs.com/2017/09/27/infinity-mirror/
- Word Clock (techniccontroller) — https://github.com/techniccontroller/think_wordclock

### スマートホーム
- ESPHome 2025.6.0 (OpenThread対応) — https://www.cnx-software.com/2025/06/24/esphome-2025-6-0-adds-esp32-p4-and-openthread-support/
- DIY mmWave Presence Detectors — https://calvin.me/diy-mmwave-presence-detectors/
- Home Assistant Voice Preview Edition (The Pi Hut) — https://thepihut.com/products/home-assistant-voice-preview-edition
- Home Assistant Voice PE (Everything Smart) — https://shop.everythingsmart.io/products/home-assistant-voice-preview-edition
- WLED: Philips Hue Integration — https://kno.wled.ge/interfaces/philips-hue/
- diyHue — https://diyhue.org/
- Automate Your Ambiance (Hackster) — https://www.hackster.io/news/automate-your-ambiance-a1670c2c3feb.amp
- HomeKey-ESP32 — http://blog.brightcoding.dev/2026/02/09/homekey-esp32-the-revolutionary-diy-smart-lock-solution
- ESP32 Smart Curtain System (Hackster) — https://www.hackster.io/news/marek-fiala-s-esp32-driven-motorized-smart-curtain-system-adapts-to-your-existing-drapes-0e2ee2fedd61
- ESP-360-REMOTE — https://github.com/ale1800/ESP-360-REMOTE
- E-ink Dashboard for Home Assistant — https://www.creatingsmarthome.com/index.php/2022/06/01/e-ink-dashboard-for-home-assistant/
- ESP32-S3-BOX-3 Customize (Home Assistant) — https://www.home-assistant.io/voice_control/s3-box-customize/

### 物理ボタン・インターフェース
- ESPHome PC Power Control — https://github.com/Erriez/ESPHomePCPowerControlHomeAssistant
- SmartKnob — https://github.com/scottbez1/smartknob
- SmartKnob README — https://github.com/scottbez1/smartknob/blob/master/README.md
- MaTouch SmartKnob — https://www.cnx-software.com/2025/02/12/matouch-smartknob-assembled-esp32-based-rotary-knob-touchscreen-display/
- Custom Smart Dial — https://hackbatch.com/custom-smart-dial/
- Adafruit MacroPad RP2040 — https://learn.adafruit.com/adafruit-macropad-rp2040
- Adafruit MacroPad RP2040 PCB (GitHub) — https://github.com/adafruit/Adafruit-MacroPad-RP2040-PCB
- deej — https://sourceforge.net/projects/deej.mirror/
- Hand Gesture Recognition (MediaPipe) — https://github.com/ahmed-0egy/Hand-Gesture-Recognition-for-Cursor-Controlling

### エッジAI・ローカルLLM
- Running Local LLMs on Pi 5 + Hailo AI HAT+ (Medium) — https://pudding-entertainment.medium.com/running-local-llms-on-raspberry-pi-5-and-hailo-ai-hat-2-b999fa240319
- NVIDIA Jetson Orin Nano Super — https://blogs.nvidia.com/blog/jetson-generative-ai-supercomputer/
- Hugging Face SO-101 / LeRobot (TechCrunch) — https://techcrunch.com/2025/04/28/hugging-face-releases-a-3d-printed-robotic-arm-starting-at-100
- SO-ARM100 (OpenELAB) — https://openelab.io/products/seeed-studio-so-arm100-pro
- SO-ARM101 (CNX Software) — https://www.cnx-software.com/2025/05/02/so-arm101-open-source-dual-robotic-arm-kit-works-with-hugging-faces-lerobot/
- Reachy Mini (VentureBeat) — https://venturebeat.com/ai/hugging-face-just-launched-a-299-robot-that-could-disrupt-the-entire-robotics-industry
- Moondream AI on Pi (Hackaday) — https://hackaday.com/tag/moondream-ai/
- Using Moondream AI to Make Your Pi "See" Like a Human — https://hackaday.com/2025/09/23/using-moondream-ai-to-make-your-pi-see-like-a-human/
- Raspberry Pi AI Vision: Moondream Setup (Geeky Gadgets) — https://www.geeky-gadgets.com/raspberry-pi-ai-vision-moondream/
- Local LLMs on Raspberry Pi (DigiKey) — https://www.digikey.com/en/maker/tutorials/2025/local-llms-on-raspberry-pi
- AI Binoculars with Bird Recognition (gagadget) — https://gagadget.com/en/ai/383062-ai-binoculars-with-bird-and-animal-recognition-unveiled-at-ces-2024-amp
- XIAO ESP32-S3 Sense TinyML (GitHub) — https://github.com/Mjrovai/XIAO-ESP32S3-Sense
- Willow — https://heywillow.io/

### レトロ・ノスタルジック
- Nixie Clock (Hackaday.io) — https://hackaday.io/project/196211-my-nixie-clock
- Nixie Clock with ESP32-C3 (Newell) — https://newell.github.io/posts/nixie-clock-esp32-c3.html
- ESP32 Nixie Clock (GitHub) — https://github.com/ThisIsntTheWay/nixie_clock
- Lixie: LED Alternative to Nixie Tube (Hackaday.io) — https://hackaday.io/project/18633-lixie-an-led-alternative-to-the-nixie-tube
- Lixie (Tindie Blog) — https://blog.tindie.com/tag/lixie/
- Lixie II (Tindie) — https://www.tindie.com/products/lixielabs/lixie-ii-the-newnixie-for-arduino-digit-kit/
- Flip-Dot Display Animation (Hackster) — https://hackster.io/news/how-to-animate-a-flip-digit-display-e9125510d8eb
- Flip Disc Display (MIT CBA) — https://fab.cba.mit.edu/classes/863.23/Harvard/people/Dunya/final_project/idea1/
- flipdotmatrix (GitHub) — https://github.com/twstokes/flipdotmatrix
- DIY Vintage Streaming Radio (Instructables) — https://www.instructables.com/DIY-Vintage-Streaming-Radio-With-a-Raspberry-Pi
- Polaroid Thermal Printer Camera (Hackster) — https://www.hackster.io/news/converting-a-polaroid-instant-camera-into-a-thermal-printer-instant-camera-with-a-raspberry-pi-ea26be468461
- Gigatron TTL Microcomputer Kit (Tindie) — https://www.tindie.com/products/johnson/gigatron-ttl-microcomputer-diy-kit/
