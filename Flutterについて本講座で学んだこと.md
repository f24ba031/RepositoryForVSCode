# Flutterについて学んだこと
# 環境設定とパッケージ構成
APIキーはOpenAIダッシュボードから取得。セキュリティのため、flutter_dotenvやenviedを使って .env に保管し、直接コードに書かないようにするのが一般的。


# 基本的なAPIリクエストフロー
messages パラメータには system, user, assistant の各 role を含め、過去の会話を渡すことで文脈を保持できる。

レスポンスの JSON 内の choices[0].message.content を取り出して画面に反映させる。

# UIとの連携
入力 (TextField) → 送信ボタン → API呼び出し → 受信レスポンスの表示、というシンプルなチャットUIの流れが基本形。

川上で送信前に吹き出しの追加・後処理 を行うことでユーザー体験が向上。

# レスポンスの高速化とUX改善
通常の onChatCompletion() に加え、ストリーミング (onChatCompletionSSE) を使うことで、逐次的にトークンを受け取ってリアルタイム表示が可能に。UXが向上し、ChatGPT公式アプリのような挙動になる。

# 使用モデルの選択肢
gpt-3.5-turbo は定番モデルだが、GPT-4 Turbo や Gemini、他社のモデル（Claude, Gemini-1.5 など）への切替も可能。各モデルの差や応答速度を試しながら選ぶのが良い。

スマホ環境では軽量なモデルやストリーミングによるUX向上が効果的。

# 統合パッケージやライブラリ

fl_chart などと組み合わせて、AI生成の内容をチャートやビジュアルにして表示するアプリも可能。

# オンデバイスLLMや音声対応
一部ではon-device LLM（LLaMA等） を Flutter で動かす取り組みもあり、オフライン対応や低遅延が期待可能。
reddit.com

音声入力・出力を統合したチャットアプリ（例：FlutterVoiceFriend）もあり、TTS/STT機能の組み込みが進んでいる。
reddit.com


