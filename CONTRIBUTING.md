# <a name="contributing-to-windows-server-technical-documentation"></a>Windows Server の技術ドキュメントに貢献する

Windows Server のテクニカルドキュメントにご関心をお寄せいただき、ありがとうございます。 お客様のフィードバック、編集、およびドキュメントへの追加をお待ちしております。Windows Server の技術コンテンツを保持する場所は2つあります。 一方の場所はパブリック (windowsserverdocs) で、もう一方はプライベート (windowsserverdocs-pr) です。 だれがどの場所に投稿するかを決定します。

- **Microsoft の従業員ではありません。** マイクロソフト以外の従業員は、公共の場所に投稿する必要があります。 その方法の詳細については、この記事の説明を参照してください。

- **私は Microsoft の従業員です。** Microsoft の従業員は、何をしようとしているかに応じて、オプションがあります。

    - **新しい記事を作成します。** 新しい記事を作成するには、GitHub アカウントとツールを作成して設定し、windowsserverdocs-pr リポジトリをフォークして複製し、リモートブランチを設定して、記事を作成し、最後に承認と発行のための新しいプル要求を作成する必要があります。 これらの手順については、GitHub を使用した [新しい Windows Server の作成に関する記事と Visual Studio Code](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/Contributor-guide/create-new-using-github.md) に関する記事をご覧ください。

    - **既存の記事に大きな変更を加えます。** 既存の記事に大幅な変更を加えるには、GitHub を使用した [既存の Windows Server の編集に関する記事と Visual Studio Code](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/Contributor-guide/edit-existing-using-github.md) の記事の手順に従ってください。

    - **既存のアーティクルに対して軽微な変更を行います。** 既存の記事に軽微な変更を加えるには、 [web ブラウザーと GitHub を使用した既存の Windows Server の更新に関する](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/Contributor-guide/github-browser-updates.md) 記事に記載されている手順に従ってください。

## <a name="sign-a-cla"></a>CLA に署名する

Microsoft の従業員では *_ない_* すべての共同作成者は、microsoft のリポジトリを編集する前に、Microsoft の [投稿者ライセンス契約 (cla) に署名](https://cla.microsoft.com/) する必要があります。 以前に Microsoft リポジトリ内で編集したことがある場合は、おめでとうございます。
この手順は既に完了しています。

## <a name="editing-topics"></a>編集 (トピックを)

既存のパブリックファイルをできるだけ簡単に編集しようとしました。

### <a name="to-edit-a-topic"></a>トピックを編集するには

1. 更新対象のページにアクセスし、[ https://docs.microsoft.com/windows-server _ * 編集] * * を選択します。

    ![GitHub Web (編集リンクを表示)](media/contribute-link.png)

2. GitHub アカウントにサインイン (またはサインアップ) します。

    トピックを編集できるページにアクセスするには、GitHub アカウントが必要です。

3. **鉛筆** アイコン (赤いボックス) を選択して、コンテンツを編集します。

    ![GitHub Web (赤いボックスに鉛筆アイコンが表示されます)](media/pencil-icon.png)

4. Markdown language を使用して、トピックに変更を加えます。 Markdown を使用してコンテンツを編集する方法の詳細については、以下を参照してください。

    - **GitHub の Microsoft 組織にリンクされている場合:** [Windows Server 共同作成者ガイド](https://github.com/MicrosoftDocs/windowsserverdocs-pr/tree/master/Contributor-guide)

    - **Microsoft の外部にいる場合:** [マスタリング Markdown](https://guides.github.com/features/mastering-markdown/)

5. 提案された変更を行い、[ **変更のプレビュー** ] を選択して、正しく表示されることを確認します。

    ![GitHub Web ([変更のプレビュー] タブを表示)](media/preview-changes.png)

6. トピックの編集が完了したら、ページの一番下までスクロールし、フォークのわかりやすい名前を入力して、[ **ファイル変更の提案** ] をクリックし、個人用 GitHub アカウントにフォークを作成します。

    ![GitHub Web ([ファイル変更の提案] ボタンを表示)](media/propose-file-change.png)

    [ **変更の比較** ] 画面が開き、フォークと元のコンテンツとの間の変更点が表示されます。

7. [ **変更の比較** ] 画面に、チェックインしているファイルに問題があるかどうかが表示されます。

    問題がない場合は、 **マージできる** というメッセージが表示されます。

    ![GitHub Web ([変更の比較] 画面を表示)](media/compare-changes.png)

8. **[pull request の作成]** を選択します。

    プル要求を使用すると、GitHub のリポジトリ内のブランチにプッシュした変更について他のユーザーに通知できます。 プル要求を開いた後は、変更がベースブランチにマージされる前に、コラボレーターによって生じる可能性のある変更について話し合い、レビューし、フォローアップコミットを追加することができます。 詳細については、「[プル要求につい](https://help.github.com/articles/about-pull-requests)て」を参照してください。

9. タイトルと説明を入力して、要求の内容についての適切なコンテキストを承認者に付与します。

10. ページの一番下までスクロールし、変更したファイルだけがこのプル要求に含まれていることを確認します。 それ以外の場合は、他のユーザーの変更を上書きすることができます。

11. プル要求を実際に送信するには、[ **プル要求の作成** ] をもう一度選択します。

    プル要求がトピックのライターに送信され、編集内容が確認されます。 要求が承認されると、更新プログラムが発行されます。

## <a name="resources"></a>参照情報

- Markdown の編集には、使い慣れたテキスト エディターを使用できます。 Microsoft の無料の軽量オープン ソース エディター、[Visual Studio Code](https://code.visualstudio.com/) をお勧めします。
