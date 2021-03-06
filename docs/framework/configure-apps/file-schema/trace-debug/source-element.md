---
title: "&lt;ソース&gt;要素"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6c5c65be8a540fdbba64d5a604c0963f9797e0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcegt-element"></a>&lt;ソース&gt;要素
トレース メッセージを開始するトレース ソースを指定します。  
  
 \<configuration>  
\<system.diagnostics >  
\<ソース >  
\<ソース >  
  
## <a name="syntax"></a>構文  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|省略可能な属性です。<br /><br /> トレース ソースの名前を指定します。|  
|`switchName`|省略可能な属性です。<br /><br /> アプリケーションでトレース スイッチのインスタンスの名前を指定します。 スイッチがで指定されていない場合、`<switches>`要素値が、スイッチのレベルを指定します。|  
|`switchType`|省略可能な属性です。<br /><br /> トレース スイッチの種類を指定します。 存在する場合、型は有効なクラス名である必要がありますされ、空の文字列にすることはできません。|  
|`extraAttribute`|省略可能な属性です。<br /><br /> によって識別されるトレース ソースに固有の属性の値を指定、<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>そのトレース ソースのメソッドです。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|収集、保管、およびメッセージをルーティングするリスナーが含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
  
## <a name="remarks"></a>コメント  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`<source>`トレース ソースを追加する要素`mySource`という名前のソース スイッチのレベルを設定して`sourceSwitch`です。 トレース情報をコンソールに出力をコンソール トレース リスナーが追加されます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [トレース スイッチ](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
