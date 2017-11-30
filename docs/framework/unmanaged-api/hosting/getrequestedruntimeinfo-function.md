---
title: "GetRequestedRuntimeInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeInfo
helpviewer_keywords: GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cca74a1ff66392608802eacedcd74bb673919e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="c5836-102">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="c5836-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="c5836-103">アプリケーションによって要求された共通言語ランタイム (CLR) のバージョンとのディレクトリ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c5836-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="c5836-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="c5836-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5836-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5836-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5836-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5836-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="c5836-107">[in]アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="c5836-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="c5836-108">[in]ランタイムのバージョン番号を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="c5836-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="c5836-109">[in]関連付けられている構成ファイルの名前`pExe`です。</span><span class="sxs-lookup"><span data-stu-id="c5836-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="c5836-110">[in]1 つ以上の[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙値。</span><span class="sxs-lookup"><span data-stu-id="c5836-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="c5836-111">[in]1 つ以上の[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列挙値。</span><span class="sxs-lookup"><span data-stu-id="c5836-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="c5836-112">[out]正常完了時にランタイムへのディレクトリ パスを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="c5836-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="c5836-113">[in]ディレクトリのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="c5836-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="c5836-114">[out]ディレクトリのパス文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5836-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c5836-115">[out]正常完了時にランタイムのバージョン番号を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="c5836-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c5836-116">[in]バージョン文字列バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="c5836-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="c5836-117">[out]バージョン文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5836-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5836-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="c5836-118">Return Value</span></span>  
 <span data-ttu-id="c5836-119">このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="c5836-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c5836-120">リターン コード</span><span class="sxs-lookup"><span data-stu-id="c5836-120">Return code</span></span>|<span data-ttu-id="c5836-121">説明</span><span class="sxs-lookup"><span data-stu-id="c5836-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c5836-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5836-122">S_OK</span></span>|<span data-ttu-id="c5836-123">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="c5836-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="c5836-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c5836-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c5836-125">ディレクトリ バッファーは、ディレクトリ パスを格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="c5836-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="c5836-126">または</span><span class="sxs-lookup"><span data-stu-id="c5836-126">- or -</span></span><br /><br /> <span data-ttu-id="c5836-127">バージョン バッファーは、バージョン文字列を保存するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="c5836-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5836-128">コメント</span><span class="sxs-lookup"><span data-stu-id="c5836-128">Remarks</span></span>  
 <span data-ttu-id="c5836-129">`GetRequestedRuntimeInfo`メソッドは、必ずしもコンピューターにインストールされている最新バージョンではないと、プロセスに読み込まれるバージョンのランタイム情報を返します。</span><span class="sxs-lookup"><span data-stu-id="c5836-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="c5836-130">.NET Framework version 2.0 を使用してインストールされている最新のバージョンに関する情報を取得できます、`GetRequestedRuntimeInfo`メソッドを次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c5836-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
-   <span data-ttu-id="c5836-131">指定して、 `pExe`、 `pwszVersion`、および`pConfigurationFile`null として使用されるパラメーター。</span><span class="sxs-lookup"><span data-stu-id="c5836-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
-   <span data-ttu-id="c5836-132">RUNTIME_INFO_UPGRADE_VERSION フラグを指定、`RUNTIME_INFO_FLAGS`の列挙体、`runtimeInfoFlags`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c5836-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="c5836-133">`GetRequestedRuntimeInfo`メソッドでは、次のような状況では、最新の CLR バージョンは返しません。</span><span class="sxs-lookup"><span data-stu-id="c5836-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
-   <span data-ttu-id="c5836-134">特定の CLR バージョンを読み込むように指定するアプリケーション構成ファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="c5836-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="c5836-135">Null を指定した場合でも、.NET Framework が構成ファイルを使用ことに注意してください、`pConfigurationFile`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c5836-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
-   <span data-ttu-id="c5836-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) CLR の以前のバージョンを指定するメソッドが呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="c5836-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
-   <span data-ttu-id="c5836-137">以前のバージョンの CLR 用にコンパイルされたアプリケーションは現在実行中です。</span><span class="sxs-lookup"><span data-stu-id="c5836-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="c5836-138">`runtimeInfoFlags`パラメーターを指定できますのみ定数のいずれかのアーキテクチャの`RUNTIME_INFO_FLAGS`一度に列挙します。</span><span class="sxs-lookup"><span data-stu-id="c5836-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
-   <span data-ttu-id="c5836-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="c5836-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="c5836-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="c5836-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="c5836-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="c5836-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5836-142">要件</span><span class="sxs-lookup"><span data-stu-id="c5836-142">Requirements</span></span>  
 <span data-ttu-id="c5836-143">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5836-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5836-144">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5836-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5836-145">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5836-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5836-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5836-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5836-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5836-147">See Also</span></span>  
 [<span data-ttu-id="c5836-148">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="c5836-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="c5836-149">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="c5836-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="c5836-150">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="c5836-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)