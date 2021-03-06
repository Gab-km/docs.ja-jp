---
title: "命令型コードに基づく検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e50c9cc756915ffc1a2f376d6b46469c85dbf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imperative-code-based-validation"></a>命令型コードに基づく検証
命令型コードに基づく検証は、アクティビティでアクティビティ自身に関する検証を可能にする簡単な方法を提供し、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティで使用できます。 検証のエラーまたは警告を判断する検証コードがアクティビティに追加されます。  
  
## <a name="using-code-based-validation"></a>コードに基づく検証の使用  
 コードに基づく検証は、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティでサポートされています。 検証コードは <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドに配置できます。また、検証エラーまたは警告はメタデータ引数に追加できます。 取得された次の例で、[基本的な検証](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md)場合のサンプル、`Cost`がより大きい、 `Price`、検証エラーがメタデータに追加します。  
  
> [!NOTE]
>  `Cost` と `Price` はこのアクティビティの引数ではありませんが、デザイン時に設定されるプロパティです。 その理由は、これらの値は <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドで検証できるためです。 引数に流入するデータの値は、データが実行時まで流れないのでデザイン時には検証できません。しかし、`RequiredArgument` 属性とオーバーロード グループを使用してアクティビティの引数を検証すると、それらの引数にバインドされていることが確認できます。 このコード例では、`RequiredArgument` 引数の `Description` 属性を確認します。これがバインドされていなければ、検証エラーが生成されます。 必須の引数は、「[ために必要な引数とオーバー ロード グループ](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)です。  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 既定では、検証エラーがメタデータに追加されるのは、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> が呼び出されたときです。 検証の警告を追加するには、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> を受け取る <xref:System.Activities.Validation.ValidationError> オーバーロードを使用し、<xref:System.Activities.Validation.ValidationError> プロパティを設定することで <xref:System.Activities.Validation.ValidationError.IsWarning%2A> が警告を表すことを示します。  
  
 検証が発生するのは、ワークフローがワークフロー デザイナーで修正され、検証エラーまたは警告がワークフロー デザイナーに表示されたときです。 ワーク フローの呼び出し時に検証も行われます。検証エラーが発生すると、既定の検証ロジックによって <xref:System.Activities.InvalidWorkflowException> がスローされます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]検証の呼び出しと、検証の警告やエラーへのアクセスを参照してください。[アクティビティの検証を呼び出す](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)です。  
  
 <xref:System.Activities.CodeActivity.CacheMetadata%2A> からスローされる例外は、検証エラーとして処理されません。 これらの例外は、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しからエスケープされ、呼び出し元によって処理される必要があります。  
  
 コードに基づく検証は、コードを含み、ワークフロー内の他のアクティビティから表示できないアクティビティを検証するときに役立ちます。 宣言の制約の検証がアクティビティとワークフローの他のアクティビティ間の関係を検証する機能を提供およびについては、[宣言の制約](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)トピックです。
