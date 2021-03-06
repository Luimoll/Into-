---
title: GitHubパッケージの支払いについて
intro: 'アカウントに含まれるストレージやデータ転送を超えて{% data variables.product.prodname_registry %}を使用したい場合は、追加の使用分が請求されます。'
product: '{% data reusables.gated-features.packages %}'
redirect_from:
  - /github/setting-up-and-managing-billing-and-payments-on-github/about-billing-for-github-packages
  - /github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages/about-billing-for-github-packages
versions:
  fpt: '*'
type: overview
topics:
  - Packages
  - Spending limits
shortTitle: 支払いについて
---

## {% data variables.product.prodname_registry %}の支払いについて

{% data reusables.package_registry.packages-billing %}

{% data reusables.package_registry.packages-spending-limit-brief %} 詳しい情報については、「[利用上限について](#about-spending-limits)」を参照してください。

{% note %}

**コンテナイメージのストレージに対する支払いの更新:** {% data variables.product.prodname_container_registry %}に対するコンテナイメージストレージと帯域幅の無料使用期間は延長されました。 {% data variables.product.prodname_container_registry %}を使用しているなら、少なくても支払い開始の1ヶ月前に通知され、支払いの予想金額の推定が示されます。 {% data variables.product.prodname_container_registry %}に関する詳しい情報については「[コンテナレジストリの利用](/packages/working-with-a-github-packages-registry/working-with-the-container-registry)」を参照してください。

{% endnote %}

Microsoft Enterprise Agreement を通じて {% data variables.product.prodname_enterprise %} を購入した場合、Azure サブスクリプション ID を Enterprise アカウントに接続して、アカウントを含む金額を超える {% data variables.product.prodname_registry %} の使用を有効にして支払うことができます。 詳しい情報については、「[Azure サブスクリプションを Enterprise に接続する](/github/setting-up-and-managing-your-enterprise/connecting-an-azure-subscription-to-your-enterprise)」を参照してください。

データ転送は毎月リセットされますが、ストレージはリセットされません。

| 製品                                                               | ストレージ | データ転送 (月あたり) |
| ---------------------------------------------------------------- | ----- | ------------ |
| {% data variables.product.prodname_free_user %}                | 500MB | 1GB          |
| {% data variables.product.prodname_pro %}                        | 2GB   | 10GB         |
| Organization の {% data variables.product.prodname_free_team %} | 500MB | 1GB          |
| {% data variables.product.prodname_team %}                       | 2GB   | 10GB         |
| {% data variables.product.prodname_ghe_cloud %}                | 50GB  | 100GB        |

{% data variables.product.prodname_actions %}によってトリガーされる送信時のデータ転送と、ソースを問わず着信時のデータ転送は無料です。 `GITHUB_TOKEN`を使用して{% data variables.product.prodname_registry %}にログインしているときは、{% data variables.product.prodname_actions %}を使用してパッケージをダウンロードしていると想定します。

|                         | ホスト利用 | セルフホスト |
| ----------------------- | ----- | ------ |
| `GITHUB_TOKEN`を使用するアクセス | 無料    | 無料     |
| パーソナルアクセストークンを使用するアクセス  | 無料    | $      |

ストレージの使用量は、ユーザ自身のアカウントで所有されているリポジトリの{% data variables.product.prodname_actions %}によって生成されるビルドアーチファクトと共有されます。 詳しい情報については、「[{% data variables.product.prodname_actions %}の支払いについて](/billing/managing-billing-for-github-actions/about-billing-for-github-actions)」を参照してください。

{% data variables.product.prodname_dotcom %}は、パッケージが公開されているリポジトリを所有するアカウントの利用状況に課金をします。 If your account's usage surpasses these limits and you have set a spending limit above $0 USD, you will pay $0.25 USD per GB of storage and $0.50 USD per GB of data transfer.

たとえば、Organizationが{% data variables.product.prodname_team %}を使用し、無制限の利用を許可しており、1か月あたりのストレージ使用量が150 GB、データ転送が50GBだった場合、そのOrganizationの当月の超過分はストレージが148GB、データ転送が40GBということです。 The storage overage would cost $0.25 USD per GB or $37 USD. The overage for data transfer would cost $0.50 USD per GB or $20 USD.

月末に、{% data variables.product.prodname_dotcom %}はデータ転送を最も近いGBに丸めます。

{% data variables.product.prodname_dotcom %}は、毎月の利用状況をその月の時間の利用状況に基づいて計算します。 たとえば、3月の10日間にストレージを3 GB使用し、3月の21日間に12GBを使用した場合、ストレージの利用状況は次のようになります。

- 3 GB x 10日 x (1日24 時間) = 720 GB時間
- 12 GB x 21日 x (1日24 時間) = 6,048 GB時間
- 720 GB時間 + 6,048 GB時間 = 6,768 GB時間
- 6,768 GB時間 / (月あたり744時間) = 9.0967 GB月

月末に、{% data variables.product.prodname_dotcom %}はストレージ使用量を最も近いGBに丸めます。 したがって、この3月のストレージ使用量は9.097 GBになります。

あなたの{% data variables.product.prodname_registry %} 利用状況は、アカウントの既存の請求日、支払い方法、領収書を共有します。 {% data reusables.dotcom_billing.view-all-subscriptions %}

{% data reusables.user_settings.context_switcher %}

## 利用上限について

{% data reusables.package_registry.packages-spending-limit-detailed %}

アカウントの利用上限の管理と変更については、「[{% data variables.product.prodname_registry %} の利用上限の管理](/billing/managing-billing-for-github-packages/managing-your-spending-limit-for-github-packages)」を参照してください。

{% data reusables.dotcom_billing.actions-packages-unpaid-account %}
