# AIコンシェルジュ「Sophia」プロジェクト概要

## 1. プロジェクトの背景と目的

### **背景**
近年、AIアシスタント技術の進歩により、音声インターフェース（VUI）や自然言語処理（NLP）を活用した対話型エージェントが急速に普及している。しかし、多くの既存のAIアシスタント（例: Alexa, Google Assistant）はクラウド依存が強く、プライバシーやカスタマイズ性の面で制約がある。

また、PC操作の自動化やIoTデバイスの制御を統合的に行えるソリューションは限られており、ユーザーの利便性向上にはまだ多くの課題が残っている。

### **目的**
本プロジェクト「Sophia」は、音声対話・PC操作・IoT制御・スクリプト実行を統合した次世代の**自律型AIコンシェルジュ**を開発することを目的とする。

- **完全なローカル動作が可能**
- **PCやスマートデバイスの制御が可能**
- **高性能な音声認識・音声合成を備える**
- **カスタマイズ性が高く、拡張しやすい**

---

## 2. システムアーキテクチャ

```
[Sophia Core] - LLMを利用したAIエージェント
   ├── 音声認識（ASR）  → Whisper / Vosk
   ├── 音声合成（TTS）  → Coqui TTS
   ├── 自然言語処理（NLP） → GPT / Rasa
   ├── PC操作（Script Executor）→ Python + Node.js
   ├── IoT連携（Home Assistant / MQTT）
   ├── キャラクター表現（VRM / Live2D）
   ├── UI（Web / Electronアプリ / モバイル）
```

---

## 3. フロントエンド構成
| 領域 | 技術 |
|------|------|
| **UIフレームワーク** | React（Next.js） |
| **デスクトップアプリ** | Electron |
| **3Dキャラクター** | VRM（Vroid） |
| **フロントエンド言語** | TypeScript |
| **状態管理** | Redux / Zustand |

---

## 4. サーバーサイド構成
| 領域 | 技術 |
|------|------|
| **Webフレームワーク** | FastAPI（Python） |
| **対話エンジン** | Rasa / GPT |
| **PCスクリプト実行** | Python（OS制御） |
| **IoT制御** | Home Assistant / MQTT |
| **データベース** | PostgreSQL / SQLite |

---

## 5. インフラ構成
| 領域 | 技術 |
|------|------|
| **クラウドオプション** | AWS / 自宅サーバー（ローカル運用推奨） |
| **音声認識** | Whisper（ローカル） |
| **音声合成** | Coqui TTS（ローカル） |
| **CI/CD** | GitHub Actions |
| **コンテナ管理** | Docker（開発環境） |

---

## 6. ディレクトリ構成（仮）
```
Sophia/
├── frontend/        # フロントエンド（Next.js / Electron）
│   ├── components/  # UIコンポーネント
│   ├── pages/       # Next.jsのページ
│   ├── assets/      # 画像、CSS、音声データ
│   ├── store/       # Zustand / Redux
│   └── public/      # 静的ファイル
│
├── backend/         # バックエンド（FastAPI / Python）
│   ├── scripts/     # スクリプト実行用
│   ├── models/      # AIモデル（Rasa / GPT）
│   ├── iot/         # IoT制御（MQTT）
│   ├── database/    # データ管理
│   └── api/         # APIエンドポイント
│
├── character/       # 3Dキャラクター制御
│   ├── vrm/         # VRMモデル
│   ├── live2d/      # Live2D関連ファイル
│   ├── animations/  # 表情・アニメーション管理
│   └── voice/       # 音声合成関連
│
├── config/          # 設定ファイル
│   ├── environment/ # 環境変数
│   ├── credentials/ # 認証情報（非公開）
│   └── logs/        # ログデータ
│
├── docs/            # ドキュメント（技術仕様書、API仕様）
└── tests/           # テストコード
```

---

## 7. 技術選定の理由

### (1) 音声処理（VUI）
| 項目 | 選定技術 | 理由 |
|------|------|------|
| **音声認識（ASR）** | Whisper（ローカル） | 高精度・無料・ローカル処理可能 |
| | Vosk（軽量） | 低スペックPCでも動作可能 |
| **音声合成（TTS）** | Coqui TTS | 高速・ローカル実行可能・カスタマイズ性 |

### (2) AIエージェント（NLP）
| 項目 | 選定技術 | 理由 |
|------|------|------|
| **対話エンジン** | Rasa | 自律的な対話が可能・ローカル実行 |
| **生成AI** | GPT（API） | 汎用性が高く、知識量が豊富 |
| | Mistral（ローカル） | プライバシー重視時に最適 |

---

## 8. 追加機能（今後の拡張）
- **WebRTC** → 通話機能追加  
- **ローカルLLM** → GPT API依存を減らす  
- **エッジAI** → Jetson NanoやRaspberry Piに最適化  

---

## 9. 結論
- **Whisper + Vosk** で **音声認識**（低遅延化）  
- **Coqui TTS** で **ローカル音声合成**（無料・高速）  
- **Rasa + GPT** で **対話管理**（拡張性あり）  
- **Python + Node.js** で **PC操作＆Web連携**（柔軟性◎）  
- **Home Assistant + MQTT** で **IoT連携**（安定＆低コスト）  
- **Electron + Next.js** で **UI開発**（クロスプラットフォーム対応）  
- **VRM + Unity** で **3Dキャラ表現**（インタラクティブ）  

→ **当技術スタックで、柔軟で高速なAIコンシェルジュ「Sophia」を再現可能とする**
