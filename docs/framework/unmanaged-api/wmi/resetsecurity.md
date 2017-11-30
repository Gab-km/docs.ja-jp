---
title: "ResetSecurity 関数 (アンマネージ API リファレンス)"
description: "ResetSecurity 関数では、現在のスレッドに偽装トークンを割り当てます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2790012a429c6a0551d8321a80570f3f8be2142b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="d0b0f-103">ResetSecurity 関数</span><span class="sxs-lookup"><span data-stu-id="d0b0f-103">ResetSecurity function</span></span>
<span data-ttu-id="d0b0f-104">指定された権限借用トークンを現在のスレッドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d0b0f-105">構文</span><span class="sxs-lookup"><span data-stu-id="d0b0f-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="d0b0f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0b0f-106">Parameters</span></span>

`token`  
<span data-ttu-id="d0b0f-107">[in]現在のスレッドに関連付ける権限借用トークンです。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="d0b0f-108">この値は `null` の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d0b0f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d0b0f-109">Return value</span></span>

<span data-ttu-id="d0b0f-110">関数が成功した場合、戻り値は`S_OK`(0) です。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="d0b0f-111">関数が失敗した場合、戻り値がゼロ以外のエラー コードです。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="d0b0f-112">拡張エラー情報を取得する呼び出し、 [GetErrorInfo](geterrorinfo.md)関数。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d0b0f-113">要件</span><span class="sxs-lookup"><span data-stu-id="d0b0f-113">Requirements</span></span>  
 <span data-ttu-id="d0b0f-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d0b0f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b0f-115">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d0b0f-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d0b0f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b0f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b0f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0b0f-117">See also</span></span>  
[<span data-ttu-id="d0b0f-118">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d0b0f-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)