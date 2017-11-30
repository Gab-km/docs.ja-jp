---
title: "ICorDebugProcess5 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5
helpviewer_keywords: ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f0a46e18121a222ee62fec207dde938d1e967b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="b64ce-102">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b64ce-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="b64ce-103">管理対象のオブジェクトのガベージ コレクションに関する情報を提供する、マネージ ヒープに対するアクセスをサポートするために ICorDebugProcess インターフェイスを拡張し、デバッガーかどうかを判断するには、アプリケーションのローカル ネイティブ イメージ キャッシュからイメージを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b64ce-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b64ce-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-104">Methods</span></span>  
  
|<span data-ttu-id="b64ce-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-105">Method</span></span>|<span data-ttu-id="b64ce-106">説明</span><span class="sxs-lookup"><span data-stu-id="b64ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b64ce-107">EnableNGenPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="b64ce-108">アプリケーションがマネージ デバッガーで実行中にネイティブ イメージを読み込む方法を決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="b64ce-109">EnumerateGCReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="b64ce-110">プロセスでガベージ コレクトされるすべてのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="b64ce-111">EnumerateHandles メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="b64ce-112">プロセスで、オブジェクト ハンドルの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="b64ce-113">EnumerateHeap メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="b64ce-114">マネージ ヒープのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="b64ce-115">EnumerateHeapRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="b64ce-116">マネージ ヒープの領域の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="b64ce-117">GetArrayLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="b64ce-118">メモリ内には、配列のレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="b64ce-119">GetGCHeapInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="b64ce-120">ポインターを取得、 [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)には、マネージ ヒープでガベージ コレクトされるオブジェクトに関する情報を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="b64ce-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="b64ce-121">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="b64ce-122">マネージ ヒープのオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="b64ce-123">GetTypeFields メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="b64ce-124">その型の識別子に基づく型のフィールド情報を格納している配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="b64ce-125">GetTypeForTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="b64ce-126">その型の識別子に基づくオブジェクトに関する情報を提供する型オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="b64ce-127">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="b64ce-128">指定したアドレスにオブジェクトの型の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="b64ce-129">GetTypeLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="b64ce-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="b64ce-130">その型の識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b64ce-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b64ce-131">コメント</span><span class="sxs-lookup"><span data-stu-id="b64ce-131">Remarks</span></span>  
 <span data-ttu-id="b64ce-132">このインターフェイスは ICorDebugProcess、ICorDebugProcess2、論理的に拡張し、 [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b64ce-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b64ce-133">このインターフェイスは、別のコンピューターとは別のプロセスでのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b64ce-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64ce-134">要件</span><span class="sxs-lookup"><span data-stu-id="b64ce-134">Requirements</span></span>  
 <span data-ttu-id="b64ce-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b64ce-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64ce-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b64ce-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b64ce-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b64ce-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b64ce-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64ce-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64ce-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="b64ce-139">See Also</span></span>  
 [<span data-ttu-id="b64ce-140">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b64ce-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b64ce-141">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b64ce-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)