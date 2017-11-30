---
title: "ICorDebugEval::NewArray メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9b5f7241e2be53cfbc2c6cea3da1b0182c3eb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="ad724-102">ICorDebugEval::NewArray メソッド</span><span class="sxs-lookup"><span data-stu-id="ad724-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="ad724-103">指定した要素の型および次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ad724-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="ad724-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="ad724-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ad724-105">使用して[icordebugeval 2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="ad724-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad724-106">構文</span><span class="sxs-lookup"><span data-stu-id="ad724-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad724-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad724-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="ad724-108">[in]配列の要素の型を指定する CorElementType 列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="ad724-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="ad724-109">[in]要素のクラスを指定する ICorDebugClass オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad724-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="ad724-110">この値を要素の型がプリミティブ型の場合は null にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="ad724-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="ad724-111">[in]配列の次元の数。</span><span class="sxs-lookup"><span data-stu-id="ad724-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="ad724-112">.NET Framework 2.0 でこの値は 1 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad724-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="ad724-113">[in]配列の各次元のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ad724-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="ad724-114">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="ad724-114">[in] Optional.</span></span> <span data-ttu-id="ad724-115">配列の各次元の下限値です。</span><span class="sxs-lookup"><span data-stu-id="ad724-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="ad724-116">この値を省略すると、各次元の下限を 0 が使われます。</span><span class="sxs-lookup"><span data-stu-id="ad724-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad724-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ad724-117">Remarks</span></span>  
 <span data-ttu-id="ad724-118">配列は常に、現在のスレッドが実行しているアプリケーション ドメインに作成します。</span><span class="sxs-lookup"><span data-stu-id="ad724-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad724-119">要件</span><span class="sxs-lookup"><span data-stu-id="ad724-119">Requirements</span></span>  
 <span data-ttu-id="ad724-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad724-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad724-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad724-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad724-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad724-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad724-123">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="ad724-123">**.NET Framework Versions:** 1.1, 1.0</span></span>