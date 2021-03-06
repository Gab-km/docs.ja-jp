---
title: "Windows フォーム DataGridView コントロールの既定の機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの既定の機能
Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロール膨大な量の既定の機能をユーザーに提供します。  
  
## <a name="default-functionality"></a>既定の機能  
 既定では、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
-   列ヘッダーおよびテーブルを垂直方向にスクロールしても表示したまま行ヘッダーを自動的に表示されます。  
  
-   現在の行の選択インジケーターを含む行ヘッダーがあります。  
  
-   最初のセルに四角形を描くを持っています。  
  
-   自動的にサイズを変更できるユーザーが列の区分線をダブルクリックすると、列があります。  
  
-   Windows XP および Windows Server 2003 ファミリで visual スタイルを自動的にサポートされるときに、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドは、アプリケーションから`Main`メソッドです。  
  
 さらの内容、<xref:System.Windows.Forms.DataGridView>コントロールは既定では編集できます。  
  
-   場合は、ユーザーは、ダブルクリックするか、セルの f2 キーを押す、コントロールは自動的にセルが編集モードにし、ユーザーの種類として、セルの内容を更新します。  
  
-   ユーザーは、グリッドの最後にスクロールする場合、新しいレコードを追加するための行が存在するユーザーが表示されます。 新しい行を追加、ユーザーは、この行をクリックすると、<xref:System.Windows.Forms.DataGridView>コントロールは、既定値を使用します。 ユーザーは、esc キーを押すと、この新しい行は表示されなくなります。  
  
-   ユーザーには、行ヘッダーがクリックすると、行全体が選択されます。  
  
 バインドすると、<xref:System.Windows.Forms.DataGridView>コントロールを設定して、データ ソースをその<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ、コントロール。  
  
-   列ヘッダーのテキストとしてデータ ソースの列の名前が自動的に使用します。  
  
-   データ ソースの内容が格納されます。 <xref:System.Windows.Forms.DataGridView>列は、データ ソース内の各列に対して自動的に作成されます。  
  
-   テーブルに 1 行ごとに表示される行のデータを作成します。  
  
-   自動的にユーザーが列見出しをクリックしたときに、基になるデータに基づく行を並べ替えます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
