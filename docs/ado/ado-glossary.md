---
title: "ADO の用語集 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1b27ecc0b3905a12d453cc53d6ac941fc80708f9
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="ado-glossary-terms"></a>ADO 用語集の用語
このトピックでは、ADO に関連する用語を定義します。

## <a name="a"></a>A
 絶対 URL、完全修飾 URL で、インターネットまたはイントラネット上にあるリソースの場所を指定します。 関連項目*URL*と*相対 URL*です。

 ActiveX では、多くの場合、要素を持つ visual か、デザイン時または実行時に自動登録すると、プロセス内の COM コンポーネントを制御します。 ActiveX コントロールには、Microsoft Internet Explorer などの Active ドキュメント コンテナーと通信する機能もがあります。

 ADISAPI (高度なデータ Internet Server Application Programming Interface) の ISAPI DLL 解析、オートメーションのコントロール、レコード セットのマーシャ リング、および MIME パッケージを提供します。 ADISAPI コンポーネントは、インターネット インフォメーション サービス (IIS) によって提供される API によって動作します。 関連項目*ISAPI*です。

 クエリ、COUNT、AVG、STDEV、テーブルの列内のすべての行を使用して値を計算するなどの関数で集計関数。 式の記述やプログラミングでは、さまざまな統計情報を決定するのに SQL 集計関数 (前述の 3 つを含む) およびドメインの集計関数を使用できます。

 エイリアス代替名の列または、SQL SELECT ステートメントで、多くの場合より短い、または意味のある式を提供します。 たとえば、次の SELECT ステートメント内の別名は、BobSales:"SalesDB から BobSales として書き込む Sales を Select"です。 DataControl オブジェクトの管理のバインドに列を動的に割り当てるには、別名を使用できます。

 アパートメント スレッドの COM スレッド モデルのオブジェクトに呼び出しはすべてここでは、1 つのスレッドで発生します。 アパートメント スレッドでは、COM は、同期され、呼び出しをマーシャ リングされます。 関連項目*COMmddefcom*です。

 操作が完了するを待たずに呼び出し元のプログラムに制御を返す操作を非同期操作です。 操作が完了する前に、コードの実行が続行されます。 関連項目*同期操作*です。

## <a name="b"></a>B
 テーブル内のフィールドと変数のエントリ、マッピングをバインドします。 ADO の Visual C 拡張機能で**Recordset**フィールドは、C と C++ の変数にマップされます。

 ビットマスク A の数値では、他のパラメーターのオプション フラグに通常の数値の値または戻り値と比較値のビット単位の対象としています。 通常この比較はビットごとの論理演算子を含むよう**と**と**または**Visual basic で **&** と**&#124;**C++ では。

 たとえば、ADO **FieldAttributeEnum**値は、フィールドの属性を確認するビットマスクとして使用できます。 フィールドが更新可能なかどうかを判断したいとします。 Visual Basic では、次の式で、これをテストできます。`Field.Attributes AND adFldUpdatable`

 結果が TRUE の場合、フィールドは更新可能です。

 ユーザーがこれにすばやく移動できますように行セット内の行を一意に識別するマーカーのブックマークを設定します。

 ビジネス オブジェクト、定義されている一連のデータの検証やビジネス ルール ロジックなどの操作を実行するオブジェクト。 ビジネス オブジェクトは、通常、中間層に常駐します。

 ビジネス ルール検証用の編集、ログオン検証、データベースの検索、ポリシー、および企業のビジネスを行う方法を構成するアルゴリズムの変換の組み合わせ。 呼ばれる*ビジネス ロジック*です。

## <a name="c"></a>C
 定数ではなく、式を式に計算されますが、その他の値によって値が決まります。 評価するには、計算式を取得して通常は他のフィールドまたは行で、その他のソースから値を計算します。

 データ ソースから行の範囲への参照を章 A。 ADO では、チャプターは、通常参照別**Recordset**です。

 チャプター列を作成することを定義すること、*親子*リレーションシップで、*親*は、**レコード セット**チャプター列を含む、 *子*は、 **Recordset**章によって表されます。

 親に章エイリアス列を参照する別名が追加されます。

 文字は、文字のセットのマッピングをその数値の値に設定します。 たとえば、Unicode は、既知のすべての文字をエンコードの対応に設定され、世界中の文字エン コード標準として使用の 16 ビット文字です。

 階層リレーションシップの従属側の子です。 子とは、上の別のノードを持つ階層構造内のノード (ルートに近い方)。 関連項目*子エイリアス*、*親子リレーションシップ*、*親*です。

 子を参照する別名を子のエイリアスです。 関連項目*エイリアス*、*子*です。

 (クラス id) の CLSID A 全体で一意の識別子 (UUID)、COM コンポーネントを識別します。 各 COM コンポーネントは、他のアプリケーションが読み込むことができるように、Windows レジストリに CLSID がします。 関連項目*ProgID*、 *COM*です。

 通常、ユーザーのデータとプロセスの入力を表示する分散システムのクライアント層 A 論理層とも呼ば、*フロント エンド*です。 通常、クライアント層、入力に基づいて、サーバーからデータを要求とし、フォーマットして結果を表示します。 関連項目*中間層*、*データ ソース層*、*分散アプリケーション*です。

 COM (コンポーネント オブジェクト モデル) A バイナリ可能にする標準相互運用するために開発された、またはどのコンピューターでの言語に関係なく、ネットワーク環境でこれらのオブジェクトが存在します。 COM ベース テクノロジには、ActiveX コントロール、自動化、およびオブジェクトのリンクと埋め込み (OLE) が含まれます。 COM は、他のコンポーネントおよびホスト アプリケーションには、その機能を公開するオブジェクトを許可します。 オブジェクトがそれ自体を公開する方法と、プロセス間やネットワークのこの公開の動作を定義します。 COM では、オブジェクトのライフ サイクルも定義します。

 COM コンポーネントのバイナリ ファイル-.dll、.ocx、一部の .exe ファイルなど、オブジェクトを提供するために COM 標準をサポートします。 このようなファイルには、1 つまたは複数クラス ファクトリ、COM クラス、レジストリ エントリのメカニズム、読み込むコードとなどのコードが含まれています。

 比較演算子、演算子を 2 つの式を比較し、ブール値を返します。

 として表現することがありますある条件パラメーター">"(より大きい)、"\<"(より小さい)、「=」(等しい)、"> ="(より大きいまたは等しい)、"< ="(以下)、"<>"(等しくない)、または「のように」(パターン一致)。

 コンポーネント データと、コードの両方をカプセル化し、公開されているサービスの適切に指定したセットを提供するオブジェクト。

 複合ファイル COM の実装には、ファイルの記憶域が構成されています。 複合ファイルが 2 つの主な要素から成る単一の構造化されたファイル内の個別のオブジェクトを格納します。 記憶域オブジェクトとストリーム オブジェクト。 同時に、ファイル内のファイル システムのような機能です。

 個々 のファイルの数が 1 つの物理ファイルに結合されます。 複合ファイル内の各ファイルは、1 つの物理ファイルの場合と同様にアクセスできます。

 定数が変化しない数値または文字列値です。 名前付きの ADO 列挙型 (列挙定数) をなど、実際の値ではなく、コードで使用できる**adUseClient**定数の値は 3 です。 (列挙 = 3)。 関連項目*列挙*です。

 カーソル レコード移動、データの更新可能性と他のユーザーがデータベースに加えられた変更の可視性を制御するデータベースの要素。

## <a name="d"></a>D
 データ オブジェクトやデータ ソースへのアプリケーションのコントロールを関連付けるためのプロセスをバインドします。 データ ソースに関連付けられているコントロールが呼び出され、*データ バインド コントロール*です。

 データ バインド コントロールの内容は、データベースの値に関連付けられます。 バインドされているグリッド コントロールなど、**レコード セット**オブジェクトには更新時に内の行、**レコード セット**更新されます。 新しい値を取得するときに、 **Recordset**、新しい値は、グリッドに表示されます。

 データ プロバイダー ソフトウェアを ADO アプリケーションにデータを公開するか、直接、またはサービス プロバイダーを介してします。 サービス プロバイダーを参照してください。

 正式な構文のデータの整形を行うため、手法を使用する (と呼ばれる**言語の整形**) を定義する特殊な**レコード セット**オブジェクト (と呼ばれる、*レコード セットの形をした*) します。データだけでなく、含まれていますが、その他への参照も**Recordset**オブジェクトや計算値に基づいて、その他の**Recordset**オブジェクト。

 データ ソース A 論理層の SQL Server データベースなどの DBMS を実行しているコンピューターを表す分散システムの。 関連項目*クライアント層*、*中間層*、*分散アプリケーション*です。

 DCOM ワイヤ プロトコルをネットワーク経由で互いと直接通信するために COM コンポーネントを有効にします。 関連項目*COM*、*コンポーネント*です。

 DDL (データ定義言語) を定義するデータの操作ではなく、SQL でこれらのステートメント。 データベースのスキーマを作成または DDL を使用して変更します。 たとえば、 **CREATE TABLE**、 **CREATE INDEX**、 **GRANT**、および**取り消す**SQL DDL ステートメントは、します。

 既定値はテキストまたはバイナリ ストリームをストリーム (によって表される、**ストリーム**オブジェクト) と関連付けられている**レコード**または**Recordset**オブジェクトを特定の OLE DB プロバイダーを使用する場合など、Microsoft OLE DB Provider for インターネットへの発行します。 通常、既定のストリームには、Web サイトのルートの HTML コードなどのファイルの内容が含まれています。

 分散アプリケーション、プログラムが、処理は、ネットワーク経由で複数のコンピューターに分けることができるように記述します。 通常、分散アプリケーションに分割されますプレゼンテーション、ビジネス ロジック、およびデータ ストアのレイヤーまたは*階層*です。 クライアント層、中間層、データ ソース層も参照してください。

 レコード セット A の切断**Recordset**を不要になったサーバーへのライブ接続を持つクライアント キャッシュのオブジェクト。 元のデータ ソースは、データの更新など、何らかの理由に再度アクセスする必要がある場合、接続が再度確立する必要があります。 ただし、コレクション、プロパティ、および、切断されている方法**Recordset**アクセスできます。

 DML (データ操作言語) 操作、データの定義ではなく、SQL でこれらのステートメント。 データベース内の値が選択され、DML を使用して変更します。 たとえば、**挿入**、**更新**、**削除**と**選択**SQL DML ステートメントは、します。

 ドキュメントのソース プロバイダー フォルダーおよびドキュメントを管理するプロバイダーの特殊なクラスです。 ドキュメントがによって表されるときに、**レコード**オブジェクト、またはドキュメントのフォルダーで表される、**レコード セット**オブジェクト、ドキュメントのソース プロバイダーが一意のフィールド セットでこれらのオブジェクトを作成します。実際のドキュメント自体ではなく、ドキュメントの特性について説明します。 リソース レコードを参照してください。

 DSN (データ ソース名) は情報のコレクションを特定の ODBC データベース アプリケーションに接続するために使用します。 ODBC ドライバー マネージャーでは、この情報を使用して、データベースへの接続を作成します。 ファイル (ファイル DSN) または Windows レジストリ (マシン DSN) では、DSN を格納できます。

 動的なプロパティ、プロパティ、データ プロバイダーまたはカーソル サービスに固有です。 **プロパティ**オブジェクトのコレクションが自動的に入力されます (「動的」) です。 特定のデータ プロバイダーを介してデータ ソースに接続されるまで、オブジェクトは動的なプロパティがありません。 参照データ プロバイダー、カーソル。

## <a name="e"></a>E
 名前付き定数の一覧を列挙します。 列挙値は一意でない必要があります。 ただしの各値の名前を列挙が定義されているスコープ内で一意にする必要があります。 ADO では、列挙型数値パラメーターの使用し、戻り値の意味を ADO コードを追加して、開発者は、数値 (バージョンを変更することがあります) を保護します。 例についてを開くには、静的な**Recordset**を使用して、 **adOpenStatic**列挙値。`Recordset.Open ,,adOpenStatic`

 呼びます*列挙型定数*です。 関連項目*定数*です。

 イベントに応答コードを記述することができます、オブジェクトが認識する操作です。 コマンドの実行、トランザクションの完了、レコード セットの移動、およびその他のアクション間でのデータ更新では、イベントを生成できます。 関連項目*イベント ハンドラー*です。

 イベント ハンドラーにイベント ハンドラーは、イベントが発生したときに実行されるコードです。 イベントを参照してください。

## <a name="h"></a>H
 一般的で比較的単純な条件またはエラーの回復またはデータの管理などの操作を管理するハンドラー A ルーチンです。

 階層のレコード セット A **Recordset**別を格納している**レコード セット**です。 データの整形、章を参照してください。

 詳細については、次を参照してください。[階層レコード セット内の行のへのアクセス](../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)です。

 一般に、階層内の階層は、top を含むランク付けされた構造体レベルし、下位レベル。 ADO では、階層的な**レコード セット**レコードとチャプターの間の親子リレーションシップを表すために使用します。 ADO でも**レコード**と**ストリーム**フォルダーおよびドキュメントのような階層ツリー構造にアクセスするオブジェクトを使用できます。 ADO MD も含まれています。**階層**OLAP キューブのディメンションのレベル間のリレーションシップを表すオブジェクト。 親子リレーションシップ、章、ツリーに階層のレコード セットを参照してください。

## <a name="i-l"></a>I-L
 インターネット サーバーでは、Microsoft® インターネット インフォメーション サービス (IIS) を実行している Windows NT® Server または Windows 2000 Server などの関数の ISAPI (Internet Server Application Programming Interface) セット。

 キーの列またはテーブル内の 1 つの行を一意に識別する列多くの場合、テーブルのインデックス化に使用されます。

## <a name="m"></a>M
 インターフェイス メソッドのパラメーターをパッケージ化、送信、およびアンパッケージ化のプロセスのスレッドまたはプロセス境界を越えてマーシャ リング。

 中間層のユーザー インターフェイスまたは Web クライアントとデータベース間で分散システムで論理層。 これは、通常のビジネス オブジェクトがインスタンス化します。 中間層は、ビジネス規則や関数が生成され、情報を受け取ると操作のコレクションです。 これを実現して、頻繁に変更できます。 アプリケーションのロジックそのものから物理的に独立しているコンポーネントをカプセル化されているビジネス ルールを使用します。 呼ばれる*アプリケーション サーバー層*です。 分散アプリケーション、クライアント層、データ ソース層も参照してください。

 MIME (多目的インターネット メール拡張子) インターネット プロトコルは、異種ネットワーク、コンピューター、および電子メール環境で豊富なコンテンツを含む電子メール メッセージの交換を許可するもともと開発。 実際には、MIME もを採用してメール以外のアプリケーションによって拡張されます。

 MIME は、バイナリ データのパブリッシュおよびインターネット上の読み取りを許可する標準です。 バイナリ データを含むファイルのヘッダーには、データの MIME の種類が含まれています。これにより、クライアント プログラム (インスタンスの Web ブラウザーやメール パッケージ) プレーン テキストの処理よりも、別の方法でデータを処理する必要があります。 たとえば、JPEG 画像を含む Web ドキュメントのヘッダーには、JPEG ファイル形式に固有の MIME の種類が含まれています。 これにより、1 つが存在する場合、JPEG ビューアーを使用してファイルを表示するブラウザーにします。

## <a name="n-o"></a>N-O
 ノード階層ツリー構造内の要素です。 ルート、または別のノードの子ノードがあります。 ノードには、複数の子の親ことができます。 階層、ツリー、ルート、子、親も参照してください。

 オブジェクトへの参照を含むオブジェクトは変数 A 変数です。 たとえば、 `objCustomObject` [customobject] の型のオブジェクトが指す変数です。`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC (Open Database Connectivity) 標準的なプログラミング言語インターフェイスは、さまざまなデータ ソースへの接続に使用されます。 これは通常、特定の ODBC ドライバーを使用するデータ ソース名 (Dsn) を割り当てることができます、コントロール パネルからアクセスします。

 OLE DB、一連のさまざまな COM を使用するソースからデータを公開するインターフェイス OLE DB インターフェイスは、多様な情報源に格納されたデータに一貫したアクセス権を持つアプリケーションを提供します。 これらのインターフェイスは、そのデータを共有できるように、データ ソースに適した DBMS 機能の容量をサポートします。 COM. も参照してください。

 オプティミスティック ロックは、編集中のレコードを含む 1 つまたは複数のレコードを含む、データ ページのロックの種類を他のユーザー レコードの中にのみ使用できなくなったによって更新される、**更新**メソッドが利用できます。呼び出しの前後に**更新**です。

 共有ロックが使用されるときに、**レコード セット**でオブジェクトを開く、 **LockType**パラメーターまたはプロパティに設定**adLockOptimistic**または**adLockBatchOptimistic**です。 排他ロックも参照してください。

 序数値注文内の項目の位置を表す数値。 ADO コレクションでは、最初の項目の序数値はゼロ (0) です。 次の項目は 1 つ (1) となどです。

## <a name="p"></a>P
 パラメーター化コマンド A するクエリまたはコマンドのコマンドが実行される前に、パラメーター値を設定することができます。 たとえば、SQL 文字列をパラメーター化できる、SQL 文字列にパラメーター マーカーを埋め込むことで (によって指定された、'?' 文字)。 アプリケーションは、各パラメーターの値を指定し、コマンドを実行します。

 親階層リレーションシップの制御側です。 階層構造では、親は、直下にある 1 つまたは複数の子ノードを階層内にあります。 親エイリアス、親子関係、子、参照してください。

 親を参照する別名を親のエイリアスです。 別名でも、親を参照してください。

 親の 1 つのレベルが 1 つ以上の子要素に関連付けられていると直接に階層構造での親子リレーションシップ A リレーションシップです。 子は低い 1 つのレベルは、1 つの親を必要とします。 親も参照してください。 子。

 排他的にロックの種類のロック、ページ編集中のレコードを含む 1 つまたは複数のレコードを持つは使用できませんの更新プログラムを作成することを確認するには、他のユーザーにします。 排他的ロックの動作は、OLE DB プロバイダーによって定義されます。 通常、レコードの編集時にロックされているし、まで使用できないまま、**更新**メソッドが完了します。

 排他ロックが有効になっているときに、**レコード セット**でオブジェクトを開く、 **LockType**パラメーターまたはプロパティに設定**adLockPessimistic**です。 オプティミスティック ロック」も参照してください。

 プールに、オブジェクトまたはデータベース接続などの事前に割り当てられたリソースのコレクションを使用してパフォーマンスを最適化します。 新しいリソースを作成するよりも、プールから既存のリソースを描画する方が効率的です。

 ProgID (プログラム識別子) A 一意の名前を COM アプリケーションによって、Windows レジストリにマップします。 ADO 接続の ProgID が"ADODB です。接続"です。 CLSID、COM. も参照してください。

 プロキシ パラメーターのマーシャ リングを提供するインターフェイス固有のオブジェクトと、クライアントで実行されている、異なる実行環境など、別のスレッドまたは別のプロセスでアプリケーション オブジェクトを呼び出すために必要な通信します。 プロキシは、クライアントであるし、呼び出されてアプリケーション オブジェクトである対応するスタブ通信します。 スタブを参照してください。

## <a name="r"></a>R
 相対 URL A は、インターネットまたはイントラネット絶対 URL または同等の ADO 接続オブジェクトで指定された開始点に対する相対位置にあるリソースを指定する URL を部分的に修飾されます。 実際、連結された絶対と相対 Url consitute 完全な URL。 URL と絶対 URL も参照してください。

 リモート データ ソースのデータ ソースをローカル システムではなく別のコンピューター上に存在する (クライアント アプリケーションが実行されます)。

 リソース レコードを定義し、フォルダーまたはドキュメントの説明のフィールドを含むドキュメントのソース プロバイダーからのレコードです。 ドキュメント自体は、リソース レコードに含まれていませんが、通常、既定のストリームまたは URL を含むリソース レコードのフィールドによってアクセスできます。 ドキュメントのソース プロバイダー、既定のストリーム、URL を参照してください。

 同じフィールドのスキーマを持つすべてのデータ ソースからの行の行セット A のセット。 行セットは、テーブルのすべてまたは一部のフィールドを表すことができます。 行セットでは、クエリまたは 2 つ以上のテーブルの結合で作成された、仮想テーブルを表すこともできます。 ADO では、行セットがによって表される**Recordset**オブジェクト。

## <a name="s"></a>S
 オブジェクトまたは変数の参照範囲、またはビューまたはテーブル内のレコードの範囲にスコープします。 たとえば、ローカル変数は、定義されたプロシージャ内でのみ参照できます。 パブリック変数は、アプリケーションで任意の場所からアクセスできます。 現在のデータベースなどのオブジェクトはスコープでは、定義済みの検索パス内にある場合です。 レコードの範囲は、多くのコマンドのスコープ句で指定できます。

 サービス プロバイダーを作成およびデータを利用してサービスをカプセル化、ADO アプリケーションの機能を拡張するソフトウェアです。 データを直接公開しないプロバイダーではなく、クエリの処理などのサービスを提供します。 サービス プロバイダーは、データ プロバイダーによって提供されるデータを処理可能性があります。 データ プロバイダーを参照してください。

 レコード セット A の形**Recordset**だけでなく、データもを他の参照 (チャプターと呼ばれる) を格納する列を持つを具体的に定義されている**Recordset**オブジェクトや計算値に基づくその他の**Recordset**オブジェクト。

 兄弟の 2 つまたは複数のノード、階層構造で、階層内の同じレベルにあります。 階層内のルート ノードには、兄弟がありません。

 ストアド プロシージャ A には、SQL ステートメントや流れ制御ステートメントは省略可能な名前を付けて保存、単位として処理などのコードのコレクションがプリコンパイル済みです。 ストアド プロシージャは、データベース内に格納されます。アプリケーションから 1 つの呼び出しで実行することができ、ユーザーが宣言した変数、条件付きの実行、およびその他の強力なプログラミング機能。

 パラメーターのマーシャ リングを提供するインターフェイスに固有のオブジェクトと別のスレッドや別のプロセスでなどの異なる実行環境で動作しているクライアントからの呼び出しを受信するアプリケーション オブジェクトの必要な通信スタブに対応します。 スタブは、アプリケーション オブジェクトであるし、それを呼び出すクライアントに位置している、対応するプロキシ通信します。 プロキシを参照してください。

 サブ ノード参照の子です。

 同期操作を次の操作の前に完了するコードによって実行される操作の開始可能性があります。 非同期操作を参照してください。

## <a name="t-z"></a>T-Z
 ツリー (ノード) の要素間の階層リレーションシップを表す構造です。 (ルート) ツリーの最上位レベルに 1 つのノードがあります。 ルートの下に、複数の子があります。 それぞれの子順番の他の子、したがってツリーのように分岐の親があります。 ドキュメントとその他のフォルダーを含むフォルダーでは、ツリー構造の一般的な例を示します。 階層ノード、ルート、子である親も参照してください。

 Web サーバーを Web サービス、およびイントラネットおよびインターネット ユーザーにページを提供するコンピューター。
