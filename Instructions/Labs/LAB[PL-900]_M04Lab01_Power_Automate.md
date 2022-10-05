---
lab:
  title: 'ラボ 4:自動化ソリューションの構築方法'
  module: 'Module 4: Get Started with Power Automate'
---

# <a name="lab-4-how-to-build-an-automated-solution"></a>ラボ 4:自動化ソリューションの構築方法

## <a name="scenario"></a>シナリオ

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

キャンパスの管理者は、建物へのアクセスがセキュリティ担当者によって管理され、すべての訪問者がホストによって事前に登録され、記録されることが要求される訪問者登録システムを近代化したいと考えています。

このコース全体を通して、アプリケーションを構築するとともに自動化を行って、ベローズ カレッジの管理担当者とセキュリティ担当者がキャンパス内の建物へのアクセスを管理および制御できるようにします。

このラボでは、訪問がスケジュールされたときに訪問者にメールを送信する Power Automate フローを作成します。

## <a name="high-level-lab-steps"></a>ラボ手順の概要

プロジェクトの完了に必要な要件は次のとおりです。

- 訪問がスケジュールされたときに、連絡先にはメールで通知する必要があります。

## <a name="prerequisites"></a>前提条件

- **モジュール 0 ラボ 0 - ラボ環境の検証**の完了
- **モジュール 2 ラボ 1 - データ モデリング**の完了
- **モジュール 2 ラボ 3 - モデル駆動型アプリを構築する方法**の完了
- 個人用メール アドレスを指定して作成した John Doe の連絡先

## <a name="exercise-1-create-visit-notification-flow"></a>演習 1:訪問通知フローを作成する

<bpt id="p1">**</bpt>Objective:<ept id="p1">**</ept> In this exercise, you will create a Power Automate flow that implements the requirement. The visitor should be sent an email that includes the unique code assigned to the visit when a visit is created.

### <a name="task-1-create-a-flow"></a>タスク \#1:フローを作成する

1.  Navigate to <ph id="ph1">&lt;https://make.powerapps.com&gt;</ph>. You may need to reauthenticate - click <bpt id="p1">**</bpt>Sign in<ept id="p1">**</ept> and follow instructions if needed.

2.  **[[自分のイニシャル] 練習]** 環境がまだ選択されていない場合は、右上で選択します。

3.  左側のナビゲーションで、**[フロー]** を選択します。

4.  メッセージが表示されたら、**[開始する]** を選択します。

5.  **[新しいフロー]** をクリックし、 **[自動クラウド フロー]** を選択します。

6.  **[フロー名]** には「訪問通知」と入力します。

7.  **[フローのトリガーを選択してください]** で、**Dataverse** を検索します。

8.  トリガー **[When a row is added, modified or deleted]\(行が追加、変更、削除されたとき\)** を選択してから、 **[作成]** をクリックします。

9.  フローのトリガー条件を設定します。

    1.  **[変更の種類]** で **[追加済み]** を選択します。

    2.  **[テーブル名]** に **[訪問]** を選択します

    3.  **[範囲]** に **[組織]** を選択します

    4.  On the trigger step, click the ellipsis (<bpt id="p1">**</bpt>...<ept id="p1">**</ept>) and click <bpt id="p2">**</bpt>Rename<ept id="p2">**</ept>. Rename this trigger <bpt id="p1">**</bpt>"When a visit is added"<ept id="p1">**</ept>. This is a good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details.

### <a name="task-2-create-a-step-to-get-the-visitor-row"></a>タスク \#2:訪問者行を取得するステップを作成する

1.  ベローズ カレッジは、キャンパス内に複数の建物を持つ教育機関です。

2.  **Dataverse** を検索します。

3.  **[ID で行を取得]** アクションを選択します。

4.  **[テーブル名]** として **[連絡先]** を選択します

5.  キャンパスの訪問者は現在、紙の日誌に記録されています。

6.  その情報は一貫して把握されておらず、キャンパス全体の訪問に関するデータを収集して分析する手段もありません。

7.  On this action, click the ellipsis (<bpt id="p1">**</bpt>...<ept id="p1">**</ept>) and click <bpt id="p2">**</bpt>Rename<ept id="p2">**</ept>.
        Rename this action <bpt id="p1">**</bpt>"Get the Visitor"<ept id="p1">**</ept>. This is a good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details.

### <a name="task-3-create-a-step-to-send-an-email-to-the-visitor"></a>タスク \#3:メールを訪問者に送信するステップを作成する

1.  Click <bpt id="p1">**</bpt>+ New step<ept id="p1">**</ept>. This is the step that will send an email to the visitor.

2.  「*メール*」を検索し、**[Office 365 Outlook]** コネクタと **[メールの送信 (V2)]** アクションを選択します。

3.  このアクションを使用するための利用規約に同意するように求められたら、**[同意する]** をクリックします。

4.  **[宛先]** フィールドの下にある **[動的なコンテンツの追加]** を選択します。 
    
5.  動的コンテンツ リストから **[電子メール]** を選択します。
        > Notice that it is beneath the **Get the visitor** header. This means you
        are selecting the Email that is related to the Visitor that you looked
        up in the previous step.

6.  **[件名]** フィールドに「**Bellows College への訪問予定**」と入力します。

7.  **メール本文**に次のテキストを入力します。

>   Dynamic content needs to be placed where fields are named in brackets. It is recommended to copy &amp; paste all text first and then add dynamic content in the correct places.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   Dear {First Name},

   You are currently scheduled to visit Bellows Campus from {Scheduled Start} until {Scheduled End}.

   Best regards,

   Campus Administration
   Bellows College
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

8.  Highlight the <bpt id="p1">**</bpt>{First Name}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>First Name<ept id="p1">**</ept> field from the <bpt id="p2">**</bpt>Get the Visitor<ept id="p2">**</ept> step.

9.  Highlight the <bpt id="p1">**</bpt>{Scheduled Start}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>Scheduled Start<ept id="p1">**</ept> field <bpt id="p2">**</bpt>When a visit is added<ept id="p2">**</ept> step.

10.  Highlight the <bpt id="p1">**</bpt>{Scheduled End}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>Scheduled End<ept id="p1">**</ept> field from the <bpt id="p2">**</bpt>When a visit is added<ept id="p2">**</ept> step.

11.  **[保存]** をクリックします。

Leave this flow tab open for the next task. You flow should look approximately like the following:

![フロー ステップの例。](media/4-Flow.png)

### <a name="task-4-validate-and-test-the-flow"></a>タスク \#4:フローを検証して、有効化する

1.  ブラウザーで新しいタブを開き、<https://make.powerapps.com> に移動します。

2.  **[[自分のイニシャル] 練習]** 環境がまだ選択されていない場合は、右上で選択します。

3.  **[アプリ]** をクリックし、前に作成した "**Bellows Campus 管理**" アプリケーションを選択します。

3.  このブラウザー タブを開いたまま、フローを使用して前のタブに戻ります。

4.  On the command bar, click <bpt id="p1">**</bpt>Test<ept id="p1">**</ept>. Select <bpt id="p1">**</bpt>Manually<ept id="p1">**</ept> and then click <bpt id="p2">**</bpt>Test<ept id="p2">**</ept>.

5.  モデル駆動型アプリを開いた状態でブラウザー タブに移動します。 

6.  左側のナビゲーションを使用して、 **[訪問者]** を選択します。

6. **[+ 新規]** ボタンを押して、新しい **[訪問者]** レコードを追加します。

7. [訪問者] レコードを次のように入力します。

    -   **名前:** テスト訪問

    -   **訪問者:** John Doe

    -   **開始予定:** 明日の午前 8 時

    -   **終了予定:** 明日の午前 9 時

8. **[保存して閉じる]** ボタンを選択します。

9. Navigate to the browser tab with your flow test running. After a short delay, you should see the flow running. This is where you can catch any issues in the flow or confirm that it ran successfully.

After a short delay, you should see an email in your inbox, since you populated John Doe's email as your personal email. Note that it may go to your Junk Email folder.

## <a name="challenges"></a>課題

- Play around with the formatting on the email. How can you make it more professional looking?