---
title: "ICorDebugThread::GetDebugState メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e66cc976be59c519e48d7ef9285963e5109d848
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="64710-102">ICorDebugThread::GetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="64710-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="64710-103">ICorDebugThread オブジェクトの現在のデバッグ状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="64710-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64710-104">構文</span><span class="sxs-lookup"><span data-stu-id="64710-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64710-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64710-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="64710-106">[out]このスレッドの現在のデバッグ状態を説明する CorDebugThreadState 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="64710-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64710-107">コメント</span><span class="sxs-lookup"><span data-stu-id="64710-107">Remarks</span></span>  
 <span data-ttu-id="64710-108">プロセスが現在停止している場合`pState`プロセス続行するか、このスレッドの実際の現在状態にない場合は、このスレッドに対して存在デバッグ状態を表します。</span><span class="sxs-lookup"><span data-stu-id="64710-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64710-109">要件</span><span class="sxs-lookup"><span data-stu-id="64710-109">Requirements</span></span>  
 <span data-ttu-id="64710-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="64710-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64710-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64710-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64710-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64710-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64710-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64710-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>