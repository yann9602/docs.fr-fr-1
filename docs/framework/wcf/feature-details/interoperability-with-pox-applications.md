---
title: "Interopérabilité avec les applications POX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf05e3327d7c99d333ab4be045e3f72e6f2a8a3f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="interoperability-with-pox-applications"></a>Interopérabilité avec les applications POX
« Plain Old XML » les applications (POX) communiquent en échangeant des messages HTTP bruts qui contiennent uniquement les données d’application XML qui ne sont pas comprises dans une enveloppe SOAP. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peut fournir les services et les clients qui utilisent des messages POX. Sur le service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être utilisé pour implémenter des services qui exposent des points de terminaison à des clients tels que les navigateurs Web et les langages de script qui envoient et reçoivent des messages POX. Sur le client, le modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être utilisé pour implémenter des clients qui communiquent avec des services reposant sur POX.  
  
> [!NOTE]
>  À l'origine, ce document a été écrit pour [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 dispose d'une prise en charge intégrée pour une utilisation avec des applications POX. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]consultez [modèle de programmation WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>Programmation POX avec WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]les services qui communiquent via HTTP à l’aide d’utilisation de messages POX un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 Cette liaison personnalisée contient deux éléments :  
  
-   Le [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) et  
  
-   Le [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
 L'encodeur de message texte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard est configuré spécialement pour utiliser la valeur <xref:System.ServiceModel.Channels.MessageVersion.None%2A>, ce qui lui permet de traiter des charges utiles de messages XML qui n'arrivent pas encapsulés dans une enveloppe SOAP.  
  
 Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui communiquent par HTTP à l'aide de messages POX utilisent une liaison semblable (illustrée dans le code impératif suivant).  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 Étant donné que les clients POX doivent spécifier explicitement les URI auxquels ils envoient des messages, ils doivent généralement configurer le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> avec un mode d'adressage manuel en affectant à la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> la valeur `true` sur l'élément. Cela permet aux messages d'être adressés explicitement par le code d'application et il n'est pas nécessaire de créer une <xref:System.ServiceModel.ChannelFactory> chaque fois qu'une application envoie un message à un URI HTTP différent.  
  
 Étant donné que les messages POX n'utilisent pas d'en-tête SOAP pour acheminer des informations de protocole importantes, les clients et les services POX doivent souvent traiter des parties de la requête HTTP sous-jacente utilisée pour envoyer ou recevoir un message. Les informations de protocole spécifiques à HTTP, telles que les en-têtes et codes d'état HTTP, sont signalées dans le modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à travers deux classes :  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, qui contient des informations à propos de la requête HTTP, telles que la méthode HTTP et les en-têtes de demande.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, qui contient des informations à propos de la réponse HTTP, telles que le code d'état HTTP et la description de l'état, ainsi que des en-têtes de réponse HTTP.  
  
 L'exemple de code suivant indique comment créer un message de demande HTTP GET adressé à http://localhost:8100/customers.  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 En premier lieu, un demande <xref:System.ServiceModel.Channels.Message> vide est créée en appelant <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. Le paramètre <xref:System.ServiceModel.Channels.MessageVersion.None%2A> est utilisé pour indiquer qu'une enveloppe SOAP n'est pas requise et le paramètre <xref:System.String.Empty> est passé comme Action. Puis le message de demande est adressé en affectant à l'en-tête <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> l'URI désiré. Ensuite, une <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> est créée et la <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> a pour valeur la méthode GET de verbe HTTP et le <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> a la valeur `true` pour indiquer qu'aucunes données ne doivent être envoyées dans le corps du message de requête HTTP sortant. Enfin, la propriété de demande est ajoutée à la collection <xref:System.ServiceModel.Channels.Message.Properties%2A> du message de demande de manière à pouvoir influencer la manière dont le transport HTTP envoie la demande. Le message est alors prêt à être envoyé sur une instance appropriée de <xref:System.ServiceModel.Channels.IRequestChannel>.  
  
 Des techniques semblables peuvent être utilisées sur le service pour extraire la <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> d'un message entrant et construire une réponse.
