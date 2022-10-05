---
lab:
  title: 'ラボ 0:ラボ環境を検証する'
  module: 'Module 0: Course introduction'
---

# <a name="lab-0-validate-lab-environment"></a>ラボ 0:ラボ環境を検証する

## <a name="scenario"></a>シナリオ

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

キャンパスの管理者は、建物へのアクセスがセキュリティ担当者によって管理され、すべての訪問者がホストによって事前に登録され、記録されることが要求される訪問者登録システムを近代化したいと考えています。

このコース全体を通して、アプリケーションを構築するとともに自動化を行って、ベローズ カレッジの管理担当者とセキュリティ担当者がキャンパス内の建物へのアクセスを管理および制御できるようにします。

In this Module 0 lab, you will acquire a Power Platform trial and access the Power Platform admin center. In the admin center, you will then create a <bpt id="p1">**</bpt>Practice<ept id="p1">**</ept> environment that you will perform the majority of your lab work in.

## <a name="exercise-1--setup"></a>演習 1 – セットアップ

### <a name="task-1---acquire-your-microsoft-power-platform-trial-tenant"></a>タスク \#1 - Microsoft Power Platform の試用版テナントを取得する

1. Authorized Lab Hoster から **Microsoft 365 の認証情報**をコピーします。

1. <https://powerapps.microsoft.com> に移動して **[無料で試す]** をクリックします。

1. **[始めましょう]** で、Microsoft 365 の認証情報の電子メール アドレスを **[職場の電子メール アドレスを入力してください]** と書かれたテキスト ボックスに入力して、 **[次へ]** をクリックします。

1. If you see a prompt that you have an existing account with Microsoft. Select <bpt id="p1">**</bpt>Sign in<ept id="p1">**</ept>.

1. Authorized Lab Hoster によって提供されたパスワードを入力し、サインインします。

1. **[はい]** を選択すると、サインインした状態になります。

1. 国を変更しないでください。

1. **[電話番号]** に「01234567890」と入力します。

1. アカウント情報を入力し、 **[作業を開始]** を選択して、Microsoft Power Platform 試用版にサインアップします。

1. 確認画面で、 **[作業の開始]** をクリックします。

1. 連絡先の詳細を入力するように求めるメッセージが表示されたら、 **[X]** をクリックしてポップアップ ウィンドウを閉じます。

### <a name="task-2--create-environment"></a>タスク \#2 – 環境を作成する

1. メッセージが表示されたら、<https://admin.powerplatform.microsoft.com> に移動し、自分の Microsoft 365 資格情報を使用してログインします。

1. ウェルカム ポップアップが表示されたら、 **[作業の開始]** をクリックします。

1. **[環境]** を選択して **[+ 新規]** をクリックします。

    1. **[名前]** に「 **<自分のイニシャル> 実習**」と入力します (例: AJ 実習)。

    1. **[タイプ]** で **[試用版]** を選択します (試用版 (サブスクリプションベース) オプションを選択しないでください)。

    1. **[この環境のデータベースを作成しますか?]** のトグルを **[はい]** にします。

    1. その他の選択はすべてデフォルトのままにして、 **[次へ]** をクリックします。

    1. 次のタブで、すべての選択を既定値のままにして、 **[保存]** をクリックします。

1. **実習**環境が環境の一覧に表示されます。

> Your environment may take a few minutes to provision. Refresh the page if needed.
