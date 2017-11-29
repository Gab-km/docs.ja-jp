---
title: "ICLRRuntimeHost::GetCLRControl メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4072c21ea002523fe8086151a40c4e17b775ebbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="ade51-102">ICLRRuntimeHost::GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="ade51-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="ade51-103">型のインターフェイス ポインターを取得[ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)ホストが共通言語ランタイム (CLR) のカスタマイズに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ade51-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade51-104">構文</span><span class="sxs-lookup"><span data-stu-id="ade51-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ade51-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ade51-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="ade51-106">[out]型のインターフェイス ポインター [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)CLR の追加の側面を構成するホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ade51-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade51-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ade51-107">Return Value</span></span>  
  
|<span data-ttu-id="ade51-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ade51-108">HRESULT</span></span>|<span data-ttu-id="ade51-109">説明</span><span class="sxs-lookup"><span data-stu-id="ade51-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ade51-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ade51-110">S_OK</span></span>|<span data-ttu-id="ade51-111">`GetCLRControl`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ade51-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="ade51-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ade51-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ade51-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ade51-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ade51-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ade51-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ade51-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ade51-115">The call timed out.</span></span>|  
|<span data-ttu-id="ade51-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ade51-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ade51-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ade51-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ade51-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ade51-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ade51-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ade51-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ade51-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ade51-120">E_FAIL</span></span>|<span data-ttu-id="ade51-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ade51-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ade51-122">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ade51-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ade51-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ade51-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ade51-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="ade51-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="ade51-125">CLR は既に開始しています。</span><span class="sxs-lookup"><span data-stu-id="ade51-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ade51-126">コメント</span><span class="sxs-lookup"><span data-stu-id="ade51-126">Remarks</span></span>  
 <span data-ttu-id="ade51-127">`ICLRControl`提供、 [GetCLRManager メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)メソッドで、ホストが、マネージャーの種類のいずれかにインターフェイス ポインターを取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ade51-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade51-128">要件</span><span class="sxs-lookup"><span data-stu-id="ade51-128">Requirements</span></span>  
 <span data-ttu-id="ade51-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ade51-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade51-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ade51-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ade51-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ade51-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ade51-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade51-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade51-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ade51-133">See Also</span></span>  
 [<span data-ttu-id="ade51-134">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ade51-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="ade51-135">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ade51-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)