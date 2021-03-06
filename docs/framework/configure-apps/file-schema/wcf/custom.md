---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 7d558be66b8a1e46d9743c5f8bf0bb9a8b4c349e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743568"
---
# <a name="ltcustomgt"></a>&lt;custom&gt;
指定自定义对等解析程序服务的设置。  
  
\<system.serviceModel>  
\<绑定 >  
\<netPeerBinding>  
\<绑定 >  
\<resolver>  
\<custom>  
  
## <a name="syntax"></a>语法  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`address`|一个 URI，指定承载自定义对等解析程序服务的对等节点的终结点地址。|  
|`resolverType`|一个字符串值，指定自定义对等解析程序服务的类型。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<标识 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定配置了此元素的自定义对等解析程序的标识。 此元素的类型为 <xref:System.ServiceModel.Configuration.IdentityElement>。|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|一个地址标头集合，可用于由自定义对等解析程序处理的 SOAP 消息。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|一个对等解析程序，可用于将对等网格 ID 解析为一组对等节点地址，这些地址表示参与网格的若干节点。|  
  
## <a name="remarks"></a>备注  
 此元素可定义自定义对等解析程序服务的基本设置，其中包括执行服务的对等解析程序的终结点地址和所有特定绑定设置。 有关创建自定义冲突解决程序的详细信息，请参阅[PeerChannel 应用程序中添加自定义冲突解决程序](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [对等解析程序](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [对等通道应用程序中添加自定义冲突解决程序](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
