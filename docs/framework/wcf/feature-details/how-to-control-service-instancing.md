---
title: "Comment&#160;: contr&#244;ler l&#39;instanciation de service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# Comment&#160;: contr&#244;ler l&#39;instanciation de service
La définition du mode d'instance d'un service vous permet de spécifier quand un <xref:System.ServiceModel.InstanceContext?displayProperty=fullName> \(et son objet de service associé, défini par l'utilisateur\) est créé.  Consultez l'énumération <xref:System.ServiceModel.InstanceContextMode> pour obtenir les modes possibles.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les comportements, consultez [Configuration et extension de l'exécution à l'aide de comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  Pour obtenir des exemples fonctionnels, consultez [Comportements](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### Pour contrôler la durée de vie de l'instance de service en utilisant du code  
  
1.  Appliquez <xref:System.ServiceModel.ServiceBehaviorAttribute> à la classe de service.  
  
2.  Affectez à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> l'une des valeurs suivantes : <xref:System.ServiceModel.InstanceContextMode>, <xref:System.ServiceModel.InstanceContextMode> ou <xref:System.ServiceModel.InstanceContextMode>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## Exemple  
 L'exemple de code suivant affecte à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> de l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> la valeur <xref:System.ServiceModel.InstanceContextMode>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>   
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>   
 <xref:System.ServiceModel.InstanceContextMode>   
 [Service: Behaviors Samples](http://msdn.microsoft.com/fr-fr/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)