---
title: "AsyncWaitHandle の使用によるアプリケーション実行のブロック"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="eb40e-102">AsyncWaitHandle の使用によるアプリケーション実行のブロック</span><span class="sxs-lookup"><span data-stu-id="eb40e-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="eb40e-103">非同期操作の結果の待機中に他の作業を続行できませんできるアプリケーションは、操作が完了するまでブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb40e-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="eb40e-104">非同期操作の完了を待機中に、アプリケーションのメイン スレッドをブロックするのにには、次のオプションのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb40e-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="eb40e-105">使用して、<xref:System.IAsyncResult.AsyncWaitHandle%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="eb40e-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="eb40e-106">この方法は、このトピックで示されています。</span><span class="sxs-lookup"><span data-stu-id="eb40e-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="eb40e-107">非同期操作の呼び出し**終了** *OperationName*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="eb40e-107">Call the asynchronous operation's **End** *OperationName* method.</span></span> <span data-ttu-id="eb40e-108">この方法は、次を参照してください。 [、非同期操作を終了してアプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb40e-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="eb40e-109">1 つまたは複数を使用するアプリケーション<xref:System.Threading.WaitHandle>非同期操作が完了するまでブロックするオブジェクトを呼び出す通常、**開始** *OperationName*メソッド、何も処理を実行します。操作と、非同期処理されるまでブロックの結果なし次のコマンドを完了します。</span><span class="sxs-lookup"><span data-stu-id="eb40e-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="eb40e-110">1 回の操作でのいずれかを呼び出すことによってアプリケーションをブロックすることができます、<xref:System.Threading.WaitHandle.WaitOne%2A>メソッドを使用して、<xref:System.IAsyncResult.AsyncWaitHandle%2A>です。</span><span class="sxs-lookup"><span data-stu-id="eb40e-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="eb40e-111">一連の非同期操作の完了を待っている間にブロックは、格納、関連付けられている<xref:System.IAsyncResult.AsyncWaitHandle%2A>オブジェクト配列の最初の呼び出しで、<xref:System.Threading.WaitHandle.WaitAll%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="eb40e-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="eb40e-112">いずれかの一連の非同期操作が完了するを待っている間にブロックは、格納、関連付けられている<xref:System.IAsyncResult.AsyncWaitHandle%2A>オブジェクト配列の最初の呼び出しで、<xref:System.Threading.WaitHandle.WaitAny%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="eb40e-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb40e-113">例</span><span class="sxs-lookup"><span data-stu-id="eb40e-113">Example</span></span>  
 <span data-ttu-id="eb40e-114">次のコード例では、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得する DNS クラスで非同期メソッドの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="eb40e-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="eb40e-115">例では、ブロックを使用して、<xref:System.Threading.WaitHandle>非同期操作に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="eb40e-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="eb40e-116">なお`null`(`Nothing` Visual Basic で) が渡されました、 <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback`と`stateObject`パラメーターこのアプローチを使用するときに、必要なこれらがないためです。</span><span class="sxs-lookup"><span data-stu-id="eb40e-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eb40e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb40e-117">See Also</span></span>  
 [<span data-ttu-id="eb40e-118">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="eb40e-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="eb40e-119">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="eb40e-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)