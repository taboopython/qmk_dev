# QMK 開発環境

このリポジトリは、Keychron K6 キーボードのための QMK ファームウェア開発環境を Docker と Docker Compose を使用して構築するためのものです。

## 前提条件

- Docker がインストールされていること
- Docker Compose がインストールされていること

## 使用方法

1. このリポジトリをクローンします。

   ```
   git clone https://github.com/your_username/qmk_dev.git
   cd qmk_dev
   ```

2. Docker Compose を使用して QMK の開発環境を構築します。

   ```
   docker-compose up -d
   ```

3. QMK の設定を行います。

   ```
   docker-compose run qmk qmk setup
   ```

4. キーマップを作成します。

   ```
   docker-compose run qmk qmk new-keymap -kb keychron/k6 -km your_keymap
   ```

5. キーマップを編集します。`keymaps/your_keymap/keymap.c`ファイルを編集してください。

6. ファームウェアをビルドします。

   ```
   docker-compose run qmk qmk compile -kb keychron/k6 -km your_keymap
   ```

7. ビルドしたファームウェアをキーボードにフラッシュします。この作業は Docker 環境外で行ってください。

## バージョン管理

このリポジトリでは、`qmk_firmware/`ディレクトリと`keymaps/`ディレクトリを Docker ボリュームとして使用しています。これらのディレクトリとその内容（特にキーマップの設定）は Git で追跡されます。

ただし、`qmk_firmware/`ディレクトリ内には QMK ファームウェアの全てのソースコードが含まれるため、その全てを追跡する必要はありません。特に、自分がカスタマイズしたキーマップ（`qmk_firmware/keyboards/keychron/k6/keymaps/your_keymap/`など）だけを追跡するようにしています。

## ライセンス

このリポジトリは MIT ライセンスの下で公開されています。詳細は[LICENSE](LICENSE)ファイルを参照してください。
