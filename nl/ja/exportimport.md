---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}。
{: tip}

# 別のワークスペースからのリソースのアップロード
{: #exportimport}

モデルの作成を加速するために、文書 (グランド・トゥルースのアノテーションがあるもの、またはないもの)、タイプ・システム、辞書など、別のワークスペースからダウンロードしたリソースをアップロードできます。
{: shortdesc}

各種のリソースを別々にダウンロードおよびアップロードできる機能により、モデルを設計および作成する際の柔軟性が増します。例えば、タイプ・システムの設計とヒューマン・アノテーションの実行のために 1 つのワークスペースを作成し、次に、機械学習モデルのトレーニングのために別のワークスペースを、ユーザーが異なっている別の {{site.data.keyword.knowledgestudioshort}} インスタンスで作成したい場合があります。ヒューマン・アノテーターによって作成されたグランド・トゥルースを含め、リソースをアップロードできる機能が、このシナリオを可能にします。

機械学習モデルのダウンロードおよびアップロードを行うことはできません。代わりに、あるワークスペースから、モデルを作成するために使用されたすべての成果物をダウンロードし、それらを新しいワークスペースにアップロードできます。その新しいワークスペースから、もう一度トレーニングを実行してモデルを再作成できます。新しいモデルと元のモデルは、同じ成果物セットでトレーニングされたため、生成する結果も似たものになるはずです。

ダウンロードするファイルは、オペレーティング・システムに依存しません。ファイルのダウンロードとアップロードが行われる {{site.data.keyword.knowledgestudioshort}} インスタンスで、同じバージョンの Linux が実行されている必要はありません。

## タイプ・システム
{: #wks_exportimport_expimp_type}

タイプ・システムをダウンロードするには、**「アセット & ツール (Assets & Tools)」** > **「エンティティー・タイプ (Entity Types)」**ページを開き、**「タイプのダウンロード (Download Types)」**をクリックします。`types-ID.json` という名前のファイルが作成され、このファイルをローカル・システムにダウンロードするように指示するプロンプトが出されます。新しいワークスペースでこのタイプ・システムを使用するには、**「エンティティー・タイプ (Entity Types)」**ページを開き、ダウンロードした `JSON` ファイルをアップロードします。

## 辞書
{: #wks_exportimport_expimp_dict}

1 つ以上の辞書をダウンロードするには、**「アセット & ツール (Assets & Tools)」** > **「プレアノテーター (Pre-annotators)」** > **「辞書 (Dictionaries)」**タブを選択し、**「辞書のダウンロード (Download Dictionaries)」**をクリックします。ダウンロードする辞書ごとに `dictionary name_timestamp.csv` という名前のファイルが作成され、それらのファイルが結合されて `workspace name_dictionary_timestamp.zip` という名前の 1 つの `ZIP` ファイルが作成され、このファイルをローカル・システムにダウンロードするように指示するプロンプトが出されます。辞書を開いて**「ダウンロード (Download)」**をクリックすることによって、個々の辞書をダウンロードすることもできます。辞書 CSV ファイルとしてアップロードしたプレビュー専用辞書をダウンロードすることはできません。

ダウンロードした辞書を新しいワークスペースにアップロードする前に、古いワークスペースからタイプ・システムをダウンロードし、それを新しいワークスペースにアップロードする必要があります。タイプ・システムと辞書は、同じ {{site.data.keyword.knowledgestudioshort}} ワークスペースからのものでなければならず、辞書をアップロードするよりも前に、新しいワークスペースにタイプ・システムが存在している必要があります。

辞書をアップロードするには、**「辞書 (Dictionaries)」**タブを開き、ダウンロードした `CSV` ファイルを追加するか、または、`ZIP` ファイルをアップロードします。

## 文書
{: #wks_exportimport_expimp_doc}

コーパスに追加した文書をダウンロードするには、**「アセット & ツール (Assets & Tools)」** > **「文書 (Documents)」** > **「文書セット (Document Sets)」**タブを開き、**「文書セットのダウンロード (Download Document Sets)」**をクリックします。`corpus-ID.zip` という名前のファイルが作成され、このファイルをローカル・システムにダウンロードするように指示するプロンプトが出されます。この `ZIP` ファイルには、コーパス内のすべての文書が含まれています。アノテーション・セットに追加されたアノテーションはこの ZIP ファイルに含まれますが、アノテーション・セットが承認されてグランド・トゥルースにプロモートされた後に限ります。

> **制限:** 事前アノテーション付けが行われた文書は、ダウンロードされるときに、読み取り不能な形式にされます。それらの文書中のヒューマン・アノテーションによって追加されたアノテーションも読み取り不能になります。

グランド・トゥルースを含む文書を新しいワークスペースにアップロードする前に、古いワークスペースからタイプ・システムをダウンロードし、それを新しいワークスペースにアップロードする必要があります。タイプ・システムと文書は、同じ {{site.data.keyword.knowledgestudioshort}} ワークスペースからのものでなければならず、グランド・トゥルース・アノテーションをアップロードするよりも前に、新しいワークスペースにタイプ・システムが存在している必要があります。

文書をアップロードするには、新しいワークスペースで**「文書セット (Document Sets)」**タブを開き、**「文書セットのアップロード (Upload Document Sets)」**をクリックし、ダウンロードしたコーパス `ZIP` ファイルを選択します。アップロードされた文書がグランド・トゥルース・アノテーションを包含するようにするのか、除外するようにするのかを指定した後、**「アップロード (Upload)」**をクリックします。文書がダウンロードされたのよりも前にグランド・トゥルースにプロモートされたアノテーションのみがアップロードされます。

**関連概念**:

[タイプ・システム](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[辞書](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[機械学習アノテーター用の文書](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[ルール・ベース・アノテーター用の文書](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)