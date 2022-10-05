---
lab:
  title: 'ラボ 2:キャンバス アプリをビルドする方法'
  module: 'Module 3: Get started with Power Apps'
---

# <a name="lab-2-how-to-build-a-canvas-app"></a>ラボ 2:キャンバス アプリをビルドする方法

## <a name="scenario"></a>シナリオ

Bellows College is an educational organization with multiple buildings on campus. Campus visits are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

Currently, campus administration is leveraging an Excel spreadsheet to track visitor registration. They would like to modernize their visitor registration system where access to the buildings is controlled by security personnel and all visits are required to be pre-registered and recorded by their hosts.

このコース全体を通して、アプリケーションを構築するとともに自動化を行って、ベローズ カレッジの管理担当者とセキュリティ担当者がキャンパス内の建物へのアクセスを管理および制御できるようにします。

## <a name="high-level-lab-steps"></a>ラボ手順の概要

キャンバス アプリを設計するには、以下の概要に従います。

- 訪問テーブルのデータからキャンバス アプリを作成する

- 訪問を参照画面に表示する方法を構成する

- アプリにいくつかの基本的な変更を加える

- アプリの機能をテストする

## <a name="prerequisites"></a>前提条件

- **モジュール 0 ラボ 0 - ラボ環境の検証**の完了
- **モジュール 2 ラボ 1 - データ モデリング**の完了

## <a name="exercise-1-create-visits-canvas-app"></a>演習 1:訪問キャンバス アプリを作成する

**目的:** この演習では、以前に作成した訪問テーブルを接続して、キャンバス アプリを作成します。

### <a name="task-1-create-the-visits-app"></a>タスク \#1:訪問アプリを作成する

1.  Navigate to <ph id="ph1">&lt;https://make.powerapps.com&gt;</ph>. You may need to reauthenticate - click <bpt id="p1">**</bpt>Sign in<ept id="p1">**</ept> and follow instructions if needed.

2.  **[[自分のイニシャル] 練習]** 環境がまだ選択されていない場合は、右上で選択します。

3.  If necessary, click the <bpt id="p1">**</bpt>Home<ept id="p1">**</ept> icon on the left side of the screen. Under the <bpt id="p1">**</bpt>Start from<ept id="p1">**</ept> section, select <bpt id="p2">**</bpt>Dataverse<ept id="p2">**</ept>.

4.  Dataverse 接続を選択します。

    > **注:** *"Dataverse 接続が存在しない場合:"*
    > - **[新しい接続]** を選択します
    > - **[Microsoft Dataverse]** を見つけます
    > - **[作成]**

5.  前のラボで作成した **[訪問]** テーブルを見つけて選択します。

6.  右下隅にある **[接続]** ボタンを選びます。

7.  アプリが作成されたら、[Power Apps Studio へようこそ] 画面で、 **[今後は表示しない]** ボックスをオンにし、 **[スキップ]** を選択します。

8.  作成が完了したら、次の図のような画面が表示されます。

![訪問データから作成されたキャンバス アプリ。](media/2-canvas-app-from-data.png)

9. ベローズ カレッジは、キャンパス内に複数の建物を持つ教育機関です。

10. 画面の右上にある **X** を選択して、アプリのプレビューを閉じます。

キャンパス訪問は現在、紙の記録簿に記録されています。

### <a name="task-2-modify-and-theme-the-newly-created-app"></a>タスク \#2:新しく作成したアプリのテーマを変更する

このタスクでは、アプリの 3 つの各画面 ([参照]、[詳細]、[編集]) のヘッダー テキストをカスタマイズし、アプリ テーマを変更します。

1.  その情報は一貫して把握されておらず、キャンパス全体の訪問に関するデータを収集して分析する手段もありません。

1.  画面の右側にある [プロパティ] タブで、**[テキスト]** コントロール プロパティを "**ベローズ カレッジの訪問**" に更新します。

1. [プロパティ] で、 **[フォント サイズ]** を **[24]** に変更します。

1.  画面の空白の背景をクリックすると、[参照] 画面に更新されたテキストが表示されます。

1.  左側のナビゲーションのツリー ビューを使用して、 **[DetailScreen1]** を選択します。

1.  画面上の **[訪問]** ラベルを選びます。

1.  画面の右側にある [プロパティ] タブで、**[テキスト]** コントロール プロパティを **"訪問の詳細"** に更新します。

1.  画面の空白の背景をクリックすると、[詳細] 画面に更新されたテキストが表示されます。

1.  左側のナビゲーションにあるツリー ビューを使用して、 **[EditScreen1]** を選びます (ツリー ビューでこれを表示するには、必要に応じて下にスクロールする必要がある場合があります)。

1.  画面上の **[訪問]** ラベルを選びます。

1.  画面の右側にある [プロパティ] タブで、**[テキスト]** コントロール プロパティのテキスト [テーブル 1] を **"詳細の編集"** に置き換えます。

1.  画面の空白の背景をクリックすると、[編集] 画面に更新されたテキストが表示されます。

1. 左側のナビゲーションにあるツリー ビューを使用して、 **[BrowseScreen1]** を選択します。

1. コマンド ツール バーで、 **[テーマ]** ボタンを選択し、表示された一覧で、テーマの色として **[赤]** を選択します。

### <a name="task-3-test-your-visits-app"></a>タスク \#3:訪問アプリをテストする

このタスクでは、新しいアプリをテストします。

1.  アプリ デザイナーでアプリケーションを開いた状態で、**[ファイル]** を選択し、アプリの名前を **[訪問アプリ]** に更新して、**[保存]** を選択します。

2.  **戻る**矢印を選んでアプリに戻ります。

3.  左側のナビゲーションを使用して、 **[参照画面 1]** を選択します。

4.  In the app designer, select the <bpt id="p1">**</bpt>preview the app<ept id="p1">**</ept> button (Play icon) on the command bar. <bpt id="p1">*</bpt>(You can also preview the app by pressing F5 on your keyboard.)<ept id="p1">*</ept>

4.  アプリが開いたら、**[項目の検索]** フィールドに、テキスト「**Maria**
     *」を入力します (検索フィールドに入力された内容に基づいて、ギャラリー内の項目がどのようにフィルター処理されるかに注目してください)。*

5.  現在、キャンパス管理では、Excel スプレッドシートを利用して訪問者の登録を追跡しています。

6.  レコードを編集するには、アプリの右上隅にある **鉛筆アイコン**を選択します。

7.  ここで [Visit Name]\(訪問名\) を編集することができます。右上隅のチェックマーク アイコンをクリックすると、変更を保存することができます。

8.  画面の右上隅にある **X** アイコンをクリックすると、キャンバス アプリ エディターに戻ります。

現在の訪問者登録システムでは、建物へのアクセスがセキュリティ担当者によって管理されており、すべての訪問を訪問先で事前に登録し、記録する必要があるため、カレッジではこのシステムを最新化したいと考えています。

## <a name="challenges"></a>課題

- [詳細画面 1] と [編集画面 1] のフォームに列 [実際の開始]、[実際の終了]、[コード]、[開始予定]、[終了予定] を追加してみましょう