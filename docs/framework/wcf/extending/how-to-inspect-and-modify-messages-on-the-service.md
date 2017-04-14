---
title: "Comment&#160;: inspecter et modifier des messages sur le service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: inspecter et modifier des messages sur le service
Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client en implémentant un <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName> et en l’insérant dans l’exécution du service. Pour plus d’informations, consultez [répartiteurs extension](../../../../docs/framework/wcf/extending/extending-dispatchers.md). La fonctionnalité équivalente sur le service est le <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>.  
  
### <a name="to-inspect-or-modify-messages"></a>Pour inspecter ou modifier des messages  
  
1.  Implémentez la <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName> interface.  
  
2.  Implémentez un <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>, ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> interface en fonction de l’étendue à laquelle vous souhaitez insérer facilement l’inspecteur de message de votre service.  
  
3.  Insérez votre comportement avant d’appeler le <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName> méthode sur le <xref:System.ServiceModel.ServiceHost?displayProperty=fullName>. Pour plus d’informations, consultez [configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants affichent, dans l'ordre :  
  
-   L'implémentation d'un inspecteur de service.  
  
-   Un comportement de service qui insère l'inspecteur.  
  
-   Un fichier de configuration qui charge et exécute le comportement dans une application de service.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code[Interceptors#9](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/hostapplication.exe.config#9)]
 [!code-csharp[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]
 [!code-vb[Interceptors#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>   
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>   
 [Configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)