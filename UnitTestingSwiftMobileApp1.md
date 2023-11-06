# UnitTest

## UnitTestとは
- 単体テストのこと
- コードの一部をテストするために作成する非常に小さな自己完結型のメソッド
- 単体テストのコードはシンプルで小さい
- 単体テストは特定の引数を使用して関数を呼び出し、テスト対象から帰ってきた結果を検証する
- 1つのテストでは、必ずん1つの機能を検証する。複数の機能を1つの単体テストで検証するのはNG
- 作成するには、XCTest Frameworkを使うのが良い。テストにクリアすると緑のチェックボックス✅が、クリアしないと赤いバツマーク❌が出る
- 単体テストはダミーのオブジェクトを使用し依存関係がないため高速で実行される
- 単体テストはネットワークに接続やデータベース操作を実行しない（これらを実行するテストは統合テスト）


## Testの種類
- 「Unit Tests（単体テスト） - Integration Tests（統合テスト） - UI Tests」の順で行われる
### Unit Tests
- すべてのテストの前に実行される。ダミーのオブジェクトを使用することで、依存関係を持たせないテスト
- ネットワークに接続やデータベース操作を実行しないため高速で実行される
- 頻繁に実行される
### Integration Tests
  - ダミーのオブジェクトが使用されず、依存関係が生じた状態で行うテスト（HTTPリクエストを送信したり、データベース操作する）
  - 外部システムと通信する必要があるため、単体テストよりも実行が遅くなる
### UItests
  - UIがちゃんと表示されるかのテスト 
  - デバイス上でアプリを実行し、ユーザーの動作をシミュレートして、アプリが期待通りに動作するかどうかをテストする



## ユニットテストのF.I.R.S.T.の原則
F.I.R.S.T.の原則を守ることで、ユニットテストの品質と効果性を高め、開発プロセス全体をスムーズに進めることができる
- F(Fast)
  - 早く動く必要がある。
  - ネットワークに接続やデータベース操作を実行しない
- I(Independent)
  - 互いに独立している、依存関係がない
  -  一つのテストが失敗しても、他のテストには影響を与えないようにすることで、問題の特定が容易になる。
- R(Repeatable)
  - 反復可能でなければならない
  - 複数回実行しても、別の環境で実行しても、同じ結果が得られる。
- S(Self-validating)
  - 自己検証。単体テストが成功したか失敗したかを知るために、開発者は何もすべきではない。
  - 単体テストは、テスト対象の関数の結果を検証し、それ自体が合格か不合格かを決定する。
  - 人間が結果をチェックする必要がないので、テストの結果の解釈が一貫する。
- T(Thorough & Timely)
  - 徹底したテスト駆動開発
  - アプリの機能の開発中に単体テストを作成する
  - コードを実稼働環境にプロモートする前に、コードを単体テストでカバーする



## テスト駆動開発
- 非テスト駆動開発は、コードを書いた後にテストを作る
- テスト駆動開発は、コードを書く前にテストを先に書く
### テスト駆動開発のライフサイクル(Red->Green->Refactor->Repeat)
- Red:失敗するテストの作成
  - 最初に新しい機能や修正をテストするためのテストケースを書く。この時点では、実際の機能や修正は実装されていないため、テストは失敗する。
- Green:テストを通過する最小限のコードの実装
  - テストケースが通過するための最小限のコードを作成する。完璧な実装よりもテストを成功させることが重要。
- Refactor:リファクタリング
  - 単体テストのコードとアプリのコードをクリーンアップして、見た目も動作も良くする。このテストが通ることを確認しながら、コードの改善をおこなうこと。再利用および改善できるコードがあるかどうかを確認
- Repeat: 前の 3 つの機能を繰り返して実装する