# Web3 DApp 開発タスクリスト

## フェーズ1: 環境構築・初期設定 🚀

### 1.1 フロントエンド環境構築
- [ ] **Web3関連依存関係の追加**
  - [ ] `@web3auth/modal` v10対応
  - [ ] `@web3auth/ethereum-provider`
  - [ ] `wagmi` + `viem`
  - [ ] `@tanstack/vue-query`
  - [ ] `@nuxtjs/tailwindcss` (UI用)

- [ ] **プロジェクト構造の構築**
  ```
  app/
  ├── components/
  │   ├── Web3/
  │   │   ├── WalletConnect.vue
  │   │   ├── TokenBalance.vue
  │   │   └── PermitSigner.vue
  │   └── UI/
  ├── composables/
  │   ├── useWeb3Auth.ts
  │   ├── useWagmi.ts
  │   └── usePermit.ts
  ├── pages/
  │   ├── index.vue
  │   ├── wallet.vue
  │   └── permit.vue
  ├── types/
  │   └── web3.ts
  └── utils/
      ├── contract.ts
      └── signature.ts
  ```

- [ ] **環境変数設定**
  - [ ] `.env.example` 作成
  - [ ] `.env` 設定
  - [ ] Web3Auth Client ID
  - [ ] RPC URLs
  - [ ] Contract Addresses

### 1.2 Nuxt3設定拡張
- [ ] **nuxt.config.ts 更新**
  - [ ] TailwindCSS設定
  - [ ] Web3モジュール設定
  - [ ] TypeScript strict mode
  - [ ] SSR/CSR設定

- [ ] **TypeScript設定強化**
  - [ ] 厳密な型チェック
  - [ ] Web3型定義

## フェーズ2: Web3Auth統合 🔐

### 2.1 Web3Auth v10移行対応
- [ ] **Modal SDK統合**
  - [ ] Web3Auth Modal初期化
  - [ ] プロバイダー設定
  - [ ] ログイン/ログアウト機能

- [ ] **認証フロー実装**
  - [ ] ソーシャルログイン対応
  - [ ] ウォレット接続状態管理
  - [ ] ユーザー情報取得

### 2.2 Metamask統合
- [ ] **Wagmi設定**
  - [ ] WagmiConfig構成
  - [ ] Chain設定 (Mainnet, Sepolia)
  - [ ] Connector設定

- [ ] **ウォレット機能**
  - [ ] Metamask検出
  - [ ] ネットワーク切り替え
  - [ ] アカウント変更監視

## フェーズ3: スマートコントラクト開発 📜

### 3.1 ERC20コントラクト設計
- [ ] **基本ERC20実装**
  ```solidity
  // MyToken.sol
  contract MyToken is ERC20, ERC20Permit, ERC20Burnable, Ownable {
      constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {
          _mint(msg.sender, 1000000 * 10 ** decimals());
      }
  }
  ```

- [ ] **Remix IDE開発**
  - [ ] コントラクト作成
  - [ ] コンパイル確認
  - [ ] テストネットデプロイ
  - [ ] ABI取得

### 3.2 Permit機能実装
- [ ] **ERC20Permit統合**
  - [ ] `permit()` 関数実装
  - [ ] nonces管理
  - [ ] domain separator設定

- [ ] **署名検証ロジック**
  - [ ] EIP-712署名フォーマット
  - [ ] `v, r, s` パラメータ分割
  - [ ] 期限チェック

## フェーズ4: フロントエンド実装 🖥️

### 4.1 UI/UXコンポーネント
- [ ] **ウォレット接続UI**
  - [ ] 接続ボタン
  - [ ] アカウント表示
  - [ ] ネットワーク状態表示

- [ ] **トークン関連UI**
  - [ ] 残高表示コンポーネント
  - [ ] 転送フォーム
  - [ ] 履歴表示

### 4.2 ERC20トークン機能
- [ ] **残高取得機能**
  - [ ] コントラクト読み取り
  - [ ] リアルタイム更新
  - [ ] ローディング状態

- [ ] **基本転送機能**
  - [ ] transfer実行
  - [ ] approve/transferFrom
  - [ ] トランザクション監視

### 4.3 Permit署名機能
- [ ] **署名生成**
  - [ ] EIP-712メッセージ作成
  - [ ] MetaMask署名要求
  - [ ] 署名データ処理

- [ ] **バックエンド連携**
  - [ ] 署名データ送信
  - [ ] API応答処理
  - [ ] エラーハンドリング

## フェーズ5: バックエンド開発 ⚙️

### 5.1 Golang API基盤
- [ ] **プロジェクト構造**
  ```
  backend/
  ├── cmd/
  │   └── server/
  ├── internal/
  │   ├── api/
  │   ├── service/
  │   ├── repository/
  │   └── config/
  ├── pkg/
  │   ├── contract/
  │   └── crypto/
  ├── contracts/
  │   └── abigen/
  └── go.mod
  ```

- [ ] **依存関係管理**
  - [ ] `go-ethereum`
  - [ ] `crypto/ecdsa`
  - [ ] `aws-sdk-go-v2/service/kms`
  - [ ] Gin/Echo framework

### 5.2 abigen統合
- [ ] **コントラクトバインディング**
  - [ ] ABI -> Go binding生成
  - [ ] コントラクトインスタンス管理
  - [ ] 読み取り/書き込み操作

- [ ] **Go-Ethereum統合**
  - [ ] Ethereum client設定
  - [ ] トランザクション送信
  - [ ] イベントログ監視

### 5.3 Permit署名処理
- [ ] **署名分割処理**
  ```go
  func SplitSignature(signature []byte) (v uint8, r, s [32]byte) {
      // v, r, s 分割ロジック実装
  }
  ```

- [ ] **KMS統合**
  - [ ] AWS KMS設定
  - [ ] 秘密鍵管理
  - [ ] 署名検証

## フェーズ6: 統合・テスト 🧪

### 6.1 フロントエンド・バックエンド統合
- [ ] **API接続**
  - [ ] RESTful API設計
  - [ ] CORS設定
  - [ ] 認証・認可

- [ ] **エラーハンドリング**
  - [ ] ネットワークエラー
  - [ ] 署名エラー
  - [ ] コントラクトエラー

### 6.2 テスト実装
- [ ] **ユニットテスト**
  - [ ] Vue component tests
  - [ ] Go service tests
  - [ ] Contract tests

- [ ] **統合テスト**
  - [ ] E2Eテスト
  - [ ] Wallet接続テスト
  - [ ] Permit署名フロー

## フェーズ7: デプロイ・運用 🚢

### 7.1 デプロイメント
- [ ] **フロントエンド**
  - [ ] Vercel/Netlify設定
  - [ ] 環境変数管理
  - [ ] ドメイン設定

- [ ] **バックエンド**
  - [ ] AWS/GCP設定
  - [ ] API Gateway設定
  - [ ] ロードバランサー

### 7.2 モニタリング
- [ ] **ログ管理**
- [ ] **パフォーマンス監視**
- [ ] **エラー追跡**

## 優先度

### 🔥 高優先度
1. Web3関連依存関係追加
2. Web3Auth設定
3. 基本ERC20コントラクト
4. ウォレット接続機能

### 🔶 中優先度
1. Permit署名機能
2. バックエンドAPI基盤
3. トークン残高表示

### 🔷 低優先度
1. 高度なUI/UX
2. パフォーマンス最適化
3. 詳細なテスト

## 注意事項

- Web3Auth v10移行ガイドに従って実装
- セキュリティベストプラクティスの遵守
- テストネットでの十分なテスト
- 秘密鍵・署名の適切な管理