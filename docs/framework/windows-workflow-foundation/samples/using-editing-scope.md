---
title: "編集スコープの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6f20ff0577e43106886f5910b8f6a69578d1b3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-editing-scope"></a>編集スコープの使用
このサンプルでは、変更のセットを 1 つの分割不可能な単位で元に戻せるように、変更のセットをバッチ処理する方法を示します。 既定では、アクティビティ デザイナー作者が実行した操作は、"元に戻す/やり直し" システムに自動的に統合されます。  
  
## <a name="demonstrates"></a>使用例  
 編集スコープ、元に戻す、およびやり直し。  
  
## <a name="discussion"></a>説明  
 このサンプルでは、1 つの作業単位内で <xref:System.Activities.Presentation.Model.ModelItem> ツリーに対する変更のセットをバッチ処理する方法を示します。 WPF デザイナーから <xref:System.Activities.Presentation.Model.ModelItem> 値に直接バインドする場合、変更が自動的に適用されることに注意してください。 このサンプルでは、1 つの変更ではなく、バッチ処理する複数の変更を命令型コードによって行うときに実行する必要がある操作を示します。  
  
 このサンプルでは、3 つのアクティビティを追加します。 編集が開始されると、<xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> が <xref:System.Activities.Presentation.Model.ModelItem> のインスタンスで呼び出されます。 この編集スコープ内で <xref:System.Activities.Presentation.Model.ModelItem> ツリーに対して行った変更を、バッチ処理します。 <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> コマンドは、このインスタンスを制御するために使用できる <xref:System.Activities.Presentation.Model.EditingScope> を返します。 <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> または <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> を呼び出して、編集スコープをコミットするか元に戻すことができます。  
  
 <xref:System.Activities.Presentation.Model.EditingScope> オブジェクトを入れ子にすることもできます。これにより、変更の複数のセットをより大きな編集スコープの一部として追跡したり、個別に制御したりできます。 この機能を使用する可能性があるシナリオとしては、複数のダイアログからの変更について、すべての変更を 1 つの分割不可能な操作として扱いながら、別々にコミットしたり元に戻したりする必要がある場合が挙げられます。 このサンプルでは、<xref:System.Collections.ObjectModel.ObservableCollection%601> 型の <xref:System.Activities.Presentation.Model.ModelEditingScope> を使用して、編集スコープをスタックします。 <xref:System.Collections.ObjectModel.ObservableCollection%601> を使用すると、デザイナー画面で入れ子の深さを確認できます。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  サンプルをビルドして実行し、左にあるボタンを使用してワークフローを変更します。  
  
2.  をクリックして**のスコープの編集を開く**です。  
  
    1.  このコマンドにより、編集スコープを作成して編集スタックにプッシュする <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> が呼び出されます。  
  
    2.  次に、選択した <xref:System.Activities.Presentation.Model.ModelItem> に 3 つのアクティビティを追加します。 編集スコープを <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> によって開かなかった場合は、3 つの新しいアクティビティがデザイナー キャンバスに表示されることに注意してください。 この操作は <xref:System.Activities.Presentation.Model.EditingScope> 内で保留中のままであるので、デザイナーはまだ更新されません。  
  
3.  キーを押して**Close Editing Scope**編集スコープをコミットします。 3 つのアクティビティがデザイナーに表示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
