---
lab:
  title: 'ラボ 5:簡単なダッシュボードを作成する方法'
  module: 'Module 5: Get Started with Power BI'
---

## <a name="lab-5-how-to-build-a-simple-dashboard"></a>ラボ 5:簡単なダッシュボードを作成する方法

## <a name="scenario"></a>シナリオ

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

キャンパスの管理者は、建物へのアクセスがセキュリティ担当者によって管理され、すべての訪問者がホストによって事前に登録され、記録されることが要求される訪問者登録システムを近代化したいと考えています。

このコース全体を通して、アプリケーションを構築するとともに自動化を行って、ベローズ カレッジの管理担当者とセキュリティ担当者がキャンパス内の建物へのアクセスを管理および制御できるようにします。

このラボでは、キャンパス訪問に関するデータを視覚化する Power BI レポートとダッシュボードをビルドします。

## <a name="high-level-lab-steps"></a>ラボ手順の概要

次の手順に従って Power BI ダッシュボードを設計および作成します。

-   キャンパス訪問情報のさまざまな視覚化を用いたレポートを作成する

-   自然言語クエリを使用して、追加で視覚化を行う

## <a name="prerequisites"></a>前提条件

- **モジュール 0 ラボ 0 - ラボ環境の検証**の完了
- **モジュール 2 ラボ 1 - データ モデリング**の完了

## <a name="things-to-consider-before-you-begin"></a>始める前に考慮すべきこと

-   このレポートが想定しているのは、どのような利用者層でしょうか?
-   How will the audience consume the report? Typical device? Location?
-   視覚化するのに十分なデータがありますか?
-   訪問に関するデータを分析するために使用できる特性は何ですか?

## <a name="exercise-1-create-power-bi-report"></a>演習 1:Power BI レポートの作成

**目的:** この演習では、前の演習で活用した Excel スプレッドシートのデータに基づいて Power BI レポートを作成します。

### <a name="task-1-prepare-power-bi-service"></a>タスク \#1:Power BI サービスを準備する

1.  [visits.pbix](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/raw/master/Allfiles/visits.pbix) をダウンロードして、コンピューターに保存します。

2.  必要に応じて、<https://app.powerbi.com/> に移動してサインインします。

3.  画面の左下隅で **[データの取得]** を選択します

4.  **[ファイル]** の **[新しいコンテンツの作成]** セクションにある **[取得]** ボタンを選択します。

5.  **[ローカル ファイル]** を選びます。

6.  以前にダウンロードした **visits.pbix** ファイルを見つけて選択します。

7.  データの読み込みが完了したら、 **[マイ ワークスペース]** を展開し、**訪問**レポートを選択します ([種類] が **[レポート]** に設定されていることに注目してください)。

8.  Click <bpt id="p1">**</bpt>Edit<ept id="p1">**</ept>. If <bpt id="p1">**</bpt>Edit<ept id="p1">**</ept> menu item is not visible click <bpt id="p2">**</bpt>...<ept id="p2">**</ept> and then select <bpt id="p3">**</bpt>Edit<ept id="p3">**</ept>.

これで、ラボで使用する Power BI サービスがセットアップされました。

### <a name="task-2-create-chart-and-time-visualizations"></a>タスク \#2:グラフと時間の視覚化を作成する

1.  **[視覚化]** パネルの "**円グラフ**" アイコンを押して、グラフを挿入します。

2.  Press the drop-down arrow beside <bpt id="p1">**</bpt>bc_building<ept id="p1">**</ept> in the Fields pane. Drag the <bpt id="p1">**</bpt>Building<ept id="p1">**</ept> field and drop it into <bpt id="p2">**</bpt>Legend<ept id="p2">**</ept> box.

3.  ベローズ カレッジは、キャンパス内に複数の建物を持つ教育機関です。

4.  コーナー ハンドルで円グラフのサイズを変更し、すべてのグラフ コンポーネントが表示されるようにします。

5.  円グラフの外側にあるレポートをクリックして選択を解除し、**視覚化** ウィンドウで 積み上げ縦棒グラフ を選択します。

6.  キャンパスの訪問者は現在、紙の日誌に記録されています。

7.  **[開始]** フィールドをドラッグして、 **[X 軸]** ターゲット ボックスにドロップします。

8.  [視覚化] ウィンドウで、 **[年]** と **[四半期]** の横にある **[x]** をクリックすると、軸に **[月]** と **[日]** の合計のみが残ります。

9.  コーナー ハンドルを使用して、必要に応じてグラフのサイズを変更します。

10. レポートがインタラクティブに動作するかをテストします。

    1.  円グラフでさまざまな積み重なったスライスをクリックし、時間レポートの変化を見てみましょう。

    2.  その情報は一貫して把握されておらず、キャンパス全体の訪問に関するデータを収集して分析する手段もありません。

    3.  円グラフの変更を確認するには、ドリルアップまたはドリルダウンして、時間縦棒グラフでさまざまなバーを選択します。

11. **[保存]** を押して進行中の作業を保存します。

## <a name="exercise-2-create-power-bi-dashboard"></a>演習 2:Power BI ダッシュボードを作成する

### <a name="task-1-create-power-bi-dashboard"></a>タスク \#1:Power BI ダッシュボードを作成する

1.  前のタスクからレポートを開く必要があります。

2.  Select <bpt id="p1">**</bpt>Pin to a dashboard<ept id="p1">**</ept> on the menu. Depending on the layout you may need to press <bpt id="p1">**</bpt>...<ept id="p1">**</ept> to show additional menu items.

3.  **[ダッシュボードにピン留めする]** プロンプトで、 **[ 新しいダッシュボード]** を選択します。

4.  **[ダッシュボード名]** として「**キャンパス管理**」と入力し、**[ライブをピン留めする]** を押します。

5.  A pop-up will prompt you that the dashboard has been created. Select <bpt id="p1">**</bpt>Go to dashboard<ept id="p1">**</ept>.

6.  表示される円グラフと棒グラフがインタラクティブに動作するかをテストします。

### <a name="task-2-add-visualizations-using-natural-language"></a>タスク \#2:自然言語を使用した視覚化の追加します。

1.  **[キャンパス管理]** ダッシュボードで 、上部の **[データ バーに関する質問]** を選択します。

2.  Enter <bpt id="p1">**</bpt>buildings by number of visits<ept id="p1">**</ept> in Q&amp;A area. A bar chart will be displayed.

3.  **[ビジュアルをピン留めする]** を選択します。

4.  **[既存のダッシュボード]** を選択し、**[キャンパス管理]** ダッシュボードを選択します。次に、**[ピン留めする]** を押します。

5.  **[Q&A を終了]** をクリックします。

Your <bpt id="p1">**</bpt>Campus Management<ept id="p1">**</ept> dashboard should be displayed with three visuals on it. You may have to scroll down to see the new Q&amp;A visual.

ダッシュボードは次のようになります。

![](media/5-powerbi-result.png)