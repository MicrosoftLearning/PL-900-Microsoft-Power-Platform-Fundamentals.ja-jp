---
lab:
  title: 'ラボ 6:Power Automate フローを作成します'
  learning path: 'Learning Path: Demonstrate the capabilities of Microsoft Power Automate'
  module: 'Module 2: Build a Microsoft Power Automate flow'
---

## 学習の目的

この演習では、学習者は Microsoft Copilot in Power Automate を使用して、一連のさまざまなクラウド フローを作成します。 Copilot や "ゼロからの作成" など、さまざまな作成方法を使用して、利用可能なさまざまなオプションに慣れましょう。

この演習を完了すると、次のことができるようになります。

- 自然言語プロンプトを使用してワークフローを設計する
- トリガーとアクションを構成する
- 実用化のために自動化をテストする。

### シナリオ

Contoso Consulting は、IT および AI コンサルティング サービスに特化したプロフェッショナル サービス組織です。 彼らは一年を通じて顧客にさまざまなイベントを提供しています。 これらのイベントの中には、多くのパートナーが参加して新製品、市場動向、サービスに関する詳細情報を提供する展示会形式のイベントもあります。 その他、年間を通じて、個々の製品に関する詳細情報を提供する短いウェビナーも開催されています。 さらに、Contoso は、顧客からの質問に対応するために自動エージェントの使用を開始しています。

Contoso は、Power Automate を使用して、顧客がイベントに登録したときに自動メールを送信する登録確認フローを構築したいと考えています。 

この演習では、特定の条件に基づいて一連の Power Automate フローを構築します。

この演習を始める前に、次のラボを完了しておく必要があります。

- **ラボ 2 - データ モデルを作成する**
- **ラボ 5 - モデル駆動型アプリを構築する**

この演習の推定所要時間は 20 から 30 分です。

## 演習 1:セッション登録通知フローを作成する

この最初の演習では、新しいセッション登録が作成されたときに自動的に実行されるフローを構築します。 登録したセッション、イベント、連絡先の詳細を取得し、登録の詳細を記載したメールをこの宛先に送信します。

### タスク 1:フローを作成する

新しく登録したユーザーには登録確認を送信します。 登録の詳細を取り込み、登録されたユーザーに確認メールを送信するフローを作成します。

1. [https://make.powerautomate.com](https://make.powerautomate.com/) に移動します。

1. 再認証が必要な場合は、**[サインイン]** を選び、必要に応じて指示に従ってください。

1. まだ選んでいない場合は、右上隅の **Dev One** 環境を選びます。 (重要: この手順を忘れなでください)。

1. 左側のナビゲーションで、**[+ 作成]** を選択します。 (プロンプトが表示されたら、**[作業の開始]** を選択します。)

1. **[自動クラウド フロー]** を選択します。

1. **[フロー名]** に「`Registration Notification`」と入力します。

1. **[フローのトリガーを選択してください]** で、`Dataverse` を検索します。

1. トリガー **[行が追加、変更、または削除されたとき]** を選んでから、**[作成]** を選びます。

    "**無効なパラメーター**" エラーが表示される場合は、認証されていないことが原因です。 以下の手順に従って接続を作成してください。 
    - **[接続の変更]** を選択します。
    - **[新規追加]** を選択します。
    - **[接続名]** フィールドに「**MOD Administrator**」と入力します。 **[認証の種類]** を **[OAuth]** のままにして、**[サインイン]** を選択します。
    - サインインしたら、「**手順 9**」に進みます。 

1. フローのトリガー条件を設定します。

    - **[変更の種類]** で **[追加済み]** を選択します。
    - **[テーブル名]** として **[Session Registrations]** を選択します。
    - トリガー ステップで、**[スコープ]** に **[組織]** を選択します。 

1. トリガー ステップの名前を `When a Session Registration is added` に変更します。

    ![セッションが追加されたときのトリガー構成のスクリーンショット](media/power-automate-01.png)

これは良い習慣であり、あなたや他のフロー編集者が詳細を深く調べることなくステップの目的を理解できるようにするものです。


### タスク 2:Registration の対象となる Event Session の詳細を取得するステップを作成します。

1. **[+ New step (+ 新しいステップ)]** を選択します。 

1. **[ID で行を取得]** を検索します。 

1. **[ID で行を取得]** アクションを選択します。

1. **[テーブル名]** として **[Event Sessions]** を選択します

1. **[行 ID]** フィールドを選びます。 **[動的コンテンツ]** または **[式]** を選択するアイコンが表示されることに注目してください。

1. **[行 ID]** フィールドで、**[動的コンテンツ]** 一覧から **[Event Session (Value)]** を選択します。 このステップでは、このフローをトリガーするために作成された **Session Registration** の **Event Session** を検索します。

1. **[ID で行を取得する]** アクションで、 この `Get the Event Session` アクションの名前を変更します

    !["Get the Event Session" アクションの構成のスクリーンショット](media/power-automate-02.png)

    次に、セッション属する Event の詳細を取得します。

1. "**Get Event Session**" ステップで、**[+ アクションの挿入]** を選択します。

1. **[ID で行を取得]** を検索します。 

1. **[ID で行を取得]** アクションを選択します。

1. **[テーブル名]** として **[Events]** を選択します

1. **[行 ID]** フィールドを選びます。 **[動的コンテンツ]** または **[式]** を選択するアイコンが表示されることに注目してください。

1. **[行 ID]** フィールドで、**[動的コンテンツ]** リストから **[Event (Value)]** を選択します。 このステップでは、前のステップで取り込まれた **Event Session** の **Event** を検索します。

1. **[ID で行を取得する]** アクションで、 このアクションの名前を `Get the Event` に変更します

    !["Get the Event" アクションの構成のスクリーンショット](media/power-automate-03a.png)

    最後に、セッションに登録されたユーザーの詳細を取得します。

1. "Get Event Details" の下にある **[新しいアクションの挿入]** を選択します。

1. 検索フィールドに「**ID で行を取得**」と入力します。

1. **[ID で行を取得]** を選択します。

1. **[テーブル名]** として **[連絡先]** を選択します

1. **[行 ID]** フィールドを選びます。 ウィンドウがポップアップ表示されます。 **[動的コンテンツ]** または **[式]** を選択します。

1. **[行 ID]** フィールドで、**[動的コンテンツ]** リストから **[When a session registration is added]** トリガーの **[Participant (Value)]** フィールドを選択します。

1. **[ID で行を取得する]** のテキストを選択し、このアクションの名前を `Get Participant Details` に変更します。

    ![[Get Participant Details] アクションの構成のスクリーンショット](media/power-automate-04a.png)

### タスク 3:セッションの登録を確認するメールを送信するステップを作成する

1. **[Get Participant Details]** ステップで、**[新しいアクションの挿入]** を選択します。

1. 検索フィールドに「**メールの送信**」と入力します。

1. **メールの送信 (V2)** を選択します。

    Outlook への接続を作成するように求められる場合があります。その場合は、**[サインイン]** ボタンを選択し、**Mod Administrator** アカウントでサインインします。 

    ![[接続の作成] 画面のスクリーンショット](media/power-automate-05.png)

1. **[宛先]** フィールドのすぐ上にある **[歯車]** アイコンを選択します。 表示されるメニューから、**[動的コンテンツの使用]** を選択します。

    ![[動的コンテンツの使用] のスクリーンショット](media/power-automate-06.png) 

1. 動的な値を使用して、**[宛先]** フィールドで、**[Get Participant Details]** の下の **[Email]** を選択します。

    ![宛先フィールドを参加者のメール アドレスに設定するスクリーンショット。](media/power-automate-07.png)

1. **[件名]** フィールドに `Registration Confirmation` と表示されていることを確認します。

1. **メール本文**に次のテキストを入力します。

    > **注:**  動的コンテンツは、フィールドが括弧で囲まれた場所に配置する必要があります。 最初にすべてのテキストをコピーして貼り付けてから、動的コンテンツを正しい場所に追加することをお勧めします。

    *`Dear {First Name}, Thank you for registering for our upcoming session {Session Name} on {Event Date}. {Speaker} will be your speaker in this session. Your session is scheduled to last {Duration (Hours)}. Check out our other session at our {Event Name}.`*

    *`Best regards,`*

    *`Events Administration`*
    
    *`Contoso Consulting`*

    次に、かっこ内のテキストを以下の項目に置き換えます。

1. **{First Name}** テキストを強調表示します。 これを、**[Get Participant Details]** ステップの **[First Name]** フィールドに置き換えます。

1. **{Session Name}** のテキストを選択します。 これを、**[Get Event Session]** ステップの **[Session Name]** フィールドに置き換えます。

1. **{Event Date}** のテキストを選択します。 これを、**[Get Event Details]** ステップの **[Event Date]** フィールドに置き換えます。

1. **{Speaker}** のテキストを選択します。 これを、**[Get Event Session]** ステップの **[Speaker (Value)]** フィールドに置き換えます。

1. **{Duration (Hours)}** のテキストを選択します。 これを、**[Get Event Session]** ステップの **[Duration (Hours)]** フィールドに置き換えます。

1. **{Event Name}** のテキストを選択します。 これを、**[Get Event Details]** ステップの **[Event Name]** フィールドに置き換えます。

    完成したステップは次の画像のようになります。

    ![完成したメールのスクリーンショット](media/power-automate-08.png)

1. **[保存]** を選択します。

    次のタスクのために、このフロー タブを開いたままにします。 フローは次のようになります。

### タスク 4:サンプル データをいくつか入力する

> **注:**  「ラボ 5 - モデル駆動型アプリを構築する」を完了している場合は、このタスクをスキップして、タスク 5 に直接進むことができます。 

1. 左側のナビゲーションを使用して、 **[アプリ]** を選択します。

1. 表示されるアプリを **[マイ アプリ]** から **[すべて]** に変更します。

1. **Event Management** アプリケーションにカーソルを合わせ、**[再生]** アイコンを選択します。

1. 左側のナビゲーションを使用して、**[Contacts]** を選択します。

1. コマンド バーで、**[+ 新規]** ボタンを選択します。

1. **[New Contact]** 画面で、次のように構成します。

    - **First Name (名):** Suzanne

    - **Last Name (姓):** Diaz

    - **役職:** エンジニア

1. フォーム ヘッダーで、**[Contact Type]** の横にある下矢印を選択します。

1. **[Contact Type]** を **[Speaker]** に設定します。
    ![フォームの [Contact Type] フィールドを設定する方法を示すスクリーンショット。](media/power-automate-09.png)

1. **[保存]** ボタンを選択して連絡先を保存し、開いたままにしておきます。

1. **[+ 新規]** をクリックします。

1. **[New Contact]** 画面で、次のように構成します。

    - **First Name (名):** Edgar

    - **Last Name (姓):** Swenson

    - **役職:** アーキテクト

    - **メール アドレス:** メール アドレスを入力します (重要。入力しないとフローが実行されません)

1. フォーム ヘッダーで、**[Contact Type]** の横にある下矢印を選択します。

1. **[Contact Type]** を **[Participant]** に設定します。

1. **保存して閉じる**ボタンを選択します。

    次に、新しいイベントを追加します。

1. 左側のナビゲーションを使用して、**[Events]** を選択します。

1. コマンド バーで、**[+ 新規]** ボタンを選択します。

1. **[New Event]** 画面で、次のように構成します。

    - **Event Name:** Spring conference.

    - **Event Date:** Tomorrow’s date.

    - **Max Attendees:** 500

    - **Event Details:** Spring conference to showcase newest products and services from our supported vendors.

    - **Event Type:** カンファレンス

    - **場所:** シアトル

    - **Registration Required:** はい/True

    ![完成した Event フォームのスクリーンショット。 ](media/power-automate-10.png)

1. **保存して閉じる**ボタンを選択します。

    次に、Event に新しいセッションを追加します。

1. 左側のナビゲーションを使用して、**[Event Sessions]** を選択します。

1. **[+ 新規]** をクリックします。

1. 次のように **[Event Session]** を構成します。

    - **Session Name:** 責任ある AI

    - **Session Date:** Tomorrow’s Date

    - **期間:** 1.5 Hours

    - **Session Description:** With all the new AI solutions, being responsible is important. We will discuss the challenges.

    - **Speaker:** Suzanne Diaz

    - **イベント:** Spring Conference

    ![完成した [Event Session] フォームのスクリーンショット。 ](media/power-automate-11.png)

1. **[保存して閉じる]** ボタンを選択します。

 
### タスク 5:フローを検証して、有効化する

1. 必要に応じてブラウザーで新しいタブを開き、[https://make.powerapps.com](https://make.powerapps.com/) に移動します。 

1. まだ選んでいない場合は、右上隅の **[Dev One]** 環境を選びます。

1. **[アプリ]** を選択し、**Contoso Event Management アプリ**を開きます。

1. このブラウザー タブを開いたまま、フローを使用して前のタブに戻ります。

1. コマンド バーの **[テスト]** を選択します。 **[手動]** を選択し、次に **[テスト]** を選択します。

1. モデル駆動型アプリを開いた状態でブラウザー タブに移動します。

    最後に、**Session Registration** を作成します。

1. 左側のナビゲーションを使用して、**[Session Registrations]** を選択します。

1. **コマンド バー**で、**[+ 新規]** を選択します。

1. 次のようにセッションの登録を完成させます。

    - **[名前]** : `E, Swenson Registration`。

    - **Registration Date:** 今日の日付

    - **Participant:** `Edgar Swenson`

    - **Session:** `Responsible AI`

    ![完成した [Session Registration] フォームのスクリーンショット。 ](media/power-automate-12.png)

1. **[保存して閉じる]** ボタンを選択します。

1. フロー テストを実行中のブラウザー タブに移動します。 しばらくすると、フローが実行されていることがわかります。 ここで、フロー内の問題をキャッチしたり、問題が正常に実行されたことを確認したりすることができます。

しばらくすると、受信トレイにメールが表示されます。

> **注:**  迷惑メール フォルダーに振り分けられる場合があります。


