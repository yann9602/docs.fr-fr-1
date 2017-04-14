---
title: "Comment&#160;: inspecter ou modifier des param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: inspecter ou modifier des param&#232;tres
Vous pouvez inspecter ou modifier les messages entrants ou sortants pour une seule opération sur un [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] objet client ou un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service en implémentant le <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName> interface et en l’insérant dans l’exécution du client ou du service. En général, un comportement d'opération est utilisé pour ajouter des inspecteurs de paramètre pour une seule opération ; d'autres comportements peuvent être utilisés pour fournir un accès aisé à l'exécution à une échelle plus grande. Pour plus d’informations, consultez [Clients extension](../../../../docs/framework/wcf/extending/extending-clients.md) et [répartiteurs extension](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Inspection ou modification de paramètres  
  
1.  Implémentez la <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName> interface.  
  
2.  Implémentez un <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> (en fonction de la portée requise) pour ajouter votre inspecteur de paramètre soit la <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=fullName> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=fullName> propriétés.  
  
3.  Insérez votre comportement avant d’appeler <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName> ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName> méthode sur le <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>. Pour plus d’informations, consultez [configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants affichent, dans l'ordre :  
  
-   Une implémentation de l'inspecteur de paramètre  
  
-   L’implémentation de comportement qui insère l’inspecteur de paramètre à l’aide un <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>et un <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>.  
  
-   Un fichier de configuration qui charge et exécute le comportement de point de terminaison dans une application cliente pour insérer l'inspecteur de paramètre sur le client  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code[Interceptors#3](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/client.exe.config#3)]
 [!code-csharp[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]
 [!code-vb[Interceptors#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/client.exe.config#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration et extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)