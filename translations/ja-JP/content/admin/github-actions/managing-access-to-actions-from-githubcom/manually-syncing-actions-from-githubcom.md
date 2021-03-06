---
title: GitHub.com からアクションを手動で同期する
intro: '{% data variables.product.prodname_dotcom_the_website %} からのアクションにアクセスする必要があるユーザは、特定のアクションを Enterprise インスタンスに同期できます。'
redirect_from:
  - /enterprise/admin/github-actions/manually-syncing-actions-from-githubcom
  - /admin/github-actions/manually-syncing-actions-from-githubcom
versions:
  ghes: '*'
  ghae: next
topics:
  - Enterprise
shortTitle: Manually sync actions
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}
{% data reusables.actions.ae-beta %}

{% data reusables.actions.enterprise-no-internet-actions %}

{% data variables.product.prodname_dotcom_the_website %} からのアクションへのアクセスを有効化する際に推奨されるアプローチは、すべてのアクションへの自動アクセスを有効化することです。 これを行うには、{% data variables.product.prodname_github_connect %} を使用して {% data variables.product.product_name %} を {% data variables.product.prodname_ghe_cloud %} と統合します。 詳しい情報については、「[{% data variables.product.prodname_github_connect %} を使用した {% data variables.product.prodname_dotcom_the_website %} アクションへの自動アクセスを有効化する](/enterprise/admin/github-actions/enabling-automatic-access-to-githubcom-actions-using-github-connect)」を参照してください。

ただし、Enterprise で許可されるアクションをより厳密に制御する場合は、このガイドに従って、{% data variables.product.company_short %} のオープンソース [`actions-sync`](https://github.com/actions/actions-sync) ツールを使用して、個々のアクションリポジトリを {% data variables.product.prodname_dotcom_the_website %} から Enterprise に同期できます。

## `actions-sync` ツールについて

`actions-sync` ツールは、{% data variables.product.prodname_dotcom_the_website %} API と {% data variables.product.product_name %} インスタンスの API にアクセスできるマシンで実行する必要があります。 両方のマシンに同時に接続する必要はありません。

マシンが両方のシステムに同時にアクセスできる場合、1 つの `actions-sync sync` コマンドで同期を実行できます。 一度に 1 つのシステムにのみアクセスできる場合は、`actions-sync pull` および `push` コマンドを使用できます。

`actions-sync` ツールは、パブリックリポジトリに保存されている {% data variables.product.prodname_dotcom_the_website %} からのみアクションをダウンロードできます。

## 必要な環境

* `actions-sync` ツールを使用する前に、すべての宛先 Organization が Enterprise にすでに存在していることを確認する必要があります。 次の例は、`synced-actions` という名前の Organization にアクションを同期する方法を示しています。 詳しい情報については、「[新しい Organization をゼロから作成する](/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)」を参照してください。
* Enterprise に、宛先 Organization のリポジトリを作成して書き込むことができる個人アクセストークン (PAT) を作成する必要があります。 詳しい情報については、「[個人アクセストークンを作成する](/github/authenticating-to-github/creating-a-personal-access-token)」を参照してください。
* {% data variables.product.product_location %} の `actions` の Organization でバンドルされたアクションを同期する場合は、`actions` の Organization の所有者である必要があります。

  {% note %}

  **注釈:** デフォルト設定では、サイト管理者であってもバンドルされた`actions` の Organization の所有者ではありません。

  {% endnote %}

  サイト管理者は、管理シェルで `ghe-org-admin-promote` コマンドを使用して、ユーザをバンドルされた`actions` の Organization の所有者に昇格させることができます。 詳しい情報については、「[管理シェル (SSH) へのアクセス](/admin/configuration/accessing-the-administrative-shell-ssh)」および「[`ghe-org-admin-promote`](/admin/configuration/command-line-utilities#ghe-org-admin-promote)」を参照してください。

  ```shell
  ghe-org-admin-promote -u <em>USERNAME</em> -o actions
  ```

## 例: `actions-sync` ツールを使用する

この例は、`actions-sync` ツールを使用して、個々のアクションを {% data variables.product.prodname_dotcom_the_website %} から Enterprise インスタンスに同期する方法を示しています。

{% note %}

**注釈:** この例では、`actions-sync sync` コマンドを使用します。これには、マシンから {% data variables.product.prodname_dotcom_the_website %} API と Enterprise インスタンスの API の両方への同時アクセスが必要です。 一度に 1 つのシステムにのみアクセスできる場合は、`actions-sync pull` および `push` コマンドを使用できます。 詳しい情報については、「[`actions/cache` README](https://github.com/actions/actions-sync#not-connected-instances)」を参照してください。

{% endnote %}

1. マシンのオペレーティングシステムの最新の [`actions-sync` リリース](https://github.com/actions/actions-sync/releases)をダウンロードして抽出します。
1. ツールのキャッシュファイルを保存するディレクトリを作成します。
1. `actions-sync sync` コマンドを実行します。

   ```shell
   ./actions-sync sync \
     --cache-dir "cache" \
     --destination-token "aabbccddeeffgg" \
     --destination-url "https://my-ghes-instance" \
     --repo-name "actions/stale:synced-actions/actions-stale"
   ```

   上記のコマンドでは、次の引数を使用しています。

   * `--cache-dir`: コマンドを実行しているマシンのキャッシュディレクトリ。
   * `--destination-token`: 宛先 Enterprise インスタンスの個人アクセストークン。
   * `--destination-url`: 宛先 Enterprise インスタンスの URL。
   * `--repo-name`: 同期するアクションリポジトリ。 これは、`owner/repository:destination_owner/destination_repository` の形式を採用しています。

     * The above example syncs the [`actions/stale`](https://github.com/actions/stale) repository to the `synced-actions/actions-stale` repository on the destination enterprise instance. 上記のコマンドを実行する前に、Enterprise で `synced-actions` という名前の Organization を作成する必要があります。
     * `:destination_owner/destination_repository` を省略すると、ツールは Enterprise の元の所有者とリポジトリ名を使用します。 コマンドを実行する前に、アクションの所有者名と一致する新しい Organization を Enterprise に作成する必要があります。 同期されたアクションを Enterprise に保存するために中枢の Organization を使用することを検討してください。これは、異なる所有者からのアクションを同期する場合、複数の新しい Organization を作成する必要がないということです。
     * `--repo-name` パラメータを `--repo-name-list` または `--repo-name-list-file` に置き換えることにより、複数のアクションを同期できます。 詳しい情報については、「[`actions/cache` README](https://github.com/actions/actions-sync#actions-sync)」を参照してください。
1. Enterprise でアクションリポジトリが作成された後、Enterprise 内のユーザは、宛先リポジトリを使用してワークフロー内のアクションを参照できます。 上記のアクション例の場合:

   ```yaml
   uses: synced-actions/actions-stale@v1
   ```

   詳しい情報については、「[GitHub Actionsのワークフロー構文](/actions/reference/workflow-syntax-for-github-actions#jobsjob_idstepsuses)」を参照してください。
