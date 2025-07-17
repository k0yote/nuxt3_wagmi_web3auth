# Web3 DApp with Nuxt3 + Web3Auth + ERC20 Gasless Permit

## プロジェクト概要
Nuxt3をベースとしたWeb3アプリケーション。Web3Auth認証、ERC20トークン、ガスレスPermit署名機能を実装。

## 技術スタック

### フロントエンド
- **Nuxt3** - Vue.jsベースのフルスタックフレームワーク
- **Web3Auth** - 認証・ウォレット管理
- **Wagmi** - Ethereum相互作用
- **MetaMask** - ウォレット接続
- **TypeScript** - 型安全性

### バックエンド
- **Golang** - バックエンドAPI
- **go-ethereum** - Ethereum相互作用
- **abigen** - Solidityコントラクトバインディング
- **AWS KMS** - 秘密鍵管理

### スマートコントラクト
- **Solidity** - コントラクト言語
- **Remix IDE** - 開発環境
- **ERC20** - トークン標準
- **ERC20Permit** - ガスレス署名
- **ERC20Burnable** - トークン焼却

## 必要な環境
- Node.js v20.12.2
- Yarn
- Go 1.21+
- Metamask拡張機能

## インストール

```bash
# 依存関係のインストール
yarn install

# 開発サーバー起動
yarn dev
```

## 開発進捗

### ✅ 完了
- [x] Nuxt3プロジェクト初期化

### 🔄 進行中
- [ ] Web3関連依存関係の追加
- [ ] プロジェクト構造の構築

### ⏳ 予定
- [ ] Web3Auth設定
- [ ] ERC20コントラクト開発
- [ ] Wagmi設定
- [ ] ガスレスPermit実装
- [ ] バックエンドAPI開発

## 設定ファイル

### Nuxt設定
- `nuxt.config.ts` - Nuxt3設定
- `package.json` - 依存関係管理

### 環境変数
- `.env` - 環境変数設定（作成予定）

## 開発ワークフロー

1. **フロントエンド開発**
   - Web3Auth統合
   - ウォレット接続機能
   - トークン残高表示
   - Permit署名機能

2. **スマートコントラクト開発**
   - ERC20トークンコントラクト
   - Permit機能実装
   - Remix IDEでのテスト

3. **バックエンド開発**
   - Golang API作成
   - 署名検証ロジック
   - KMS統合

## 参考リンク
- [Web3Auth Migration Guide](https://web3auth.io/docs/migration-guides/no-modal-v9-to-v10#enterprise-menu)
- [Nuxt3 Documentation](https://nuxt.com/docs)
- [Wagmi Documentation](https://wagmi.sh/)
