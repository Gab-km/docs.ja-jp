---
title: "方法 : データベース値を上書きすることで競合を解決する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1dd9a6be51ad1723aab7c3102387a42d1c24996
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>方法 : データベース値を上書きすることで競合を解決する
変更を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用してデータベース内の値を上書きできます。 詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。  
  
> [!NOTE]
>  どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。 この処理によって、次の更新処理が同じ同時実行チェックで失敗することを防止できます。  
  
## <a name="example"></a>例  
 このシナリオでは、ユーザー 1 が変更を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。これは、途中でユーザー 2 が Assistant 列と Department 列を変更していたためです。 次の表は、この状況を示しています。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態|Alfreds|Maria|Sales|  
|ユーザー 1 が送信しようとした変更内容|Alfred||Marketing|  
|ユーザー 2 が既に送信した変更内容||Mary|サービス|  
  
 ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値で上書きすることに決めます。  
  
 ユーザー 1 が <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用して競合を解決すると、データベース内の結果は次の表のようになります。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|競合解決後の新しい状態|Alfred<br /><br /> (ユーザー 1 の値)|Maria<br /><br /> (元の値)|Marketing<br /><br /> (ユーザー 1 の値)|  
  
 次のコード例は、データベース値を現在のクライアント メンバー値で上書きする方法を示しています  (個々のメンバーの競合に対する検査やカスタム ハンドリングは行われません)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>参照  
 [方法 : 変更の競合を管理する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
