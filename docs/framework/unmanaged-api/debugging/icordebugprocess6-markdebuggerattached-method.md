---
title: "ICorDebugProcess6::MarkDebuggerAttached メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="87c70-102">ICorDebugProcess6::MarkDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="87c70-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="87c70-103">.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="87c70-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c70-104">構文</span><span class="sxs-lookup"><span data-stu-id="87c70-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87c70-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87c70-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="87c70-106">`true` メソッドが、デバッガーが接続されていることを示す必要がある場合は、<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>。それ以外の場合は、`false`。</span><span class="sxs-lookup"><span data-stu-id="87c70-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87c70-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="87c70-107">Return Value</span></span>  
 <span data-ttu-id="87c70-108">メソッドは、次の表に記載されている値を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="87c70-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="87c70-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="87c70-109">Return value</span></span>|<span data-ttu-id="87c70-110">説明</span><span class="sxs-lookup"><span data-stu-id="87c70-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="87c70-111">デバッグ対象は正常に更新されました。</span><span class="sxs-lookup"><span data-stu-id="87c70-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="87c70-112"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドを格納するアセンブリが読み込まれていないか、メタデータの欠落などの他のエラーが原因で認識されません。</span><span class="sxs-lookup"><span data-stu-id="87c70-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="87c70-113">このエラーは一般的なもので、問題ありません。</span><span class="sxs-lookup"><span data-stu-id="87c70-113">This error is common and benign.</span></span> <span data-ttu-id="87c70-114">追加のアセンブリを読み込むときに、再度メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="87c70-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="87c70-115">その他の失敗した `HRESULT` 値。</span><span class="sxs-lookup"><span data-stu-id="87c70-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="87c70-116">可能性が高いその他の値は、不適切に動作するデバッガーまたはコンパイラ コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="87c70-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87c70-117">コメント</span><span class="sxs-lookup"><span data-stu-id="87c70-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87c70-118">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="87c70-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c70-119">要件</span><span class="sxs-lookup"><span data-stu-id="87c70-119">Requirements</span></span>  
 <span data-ttu-id="87c70-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87c70-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c70-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87c70-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87c70-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87c70-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87c70-123">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c70-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c70-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="87c70-124">See Also</span></span>  
 [<span data-ttu-id="87c70-125">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87c70-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="87c70-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="87c70-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)