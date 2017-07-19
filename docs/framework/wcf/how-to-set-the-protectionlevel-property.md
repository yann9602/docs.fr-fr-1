---
title: "Comment&#160;: d&#233;finir la propri&#233;t&#233; ProtectionLevel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ProtectionLevel (propriété)"
  - "WCF, sécurité"
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;finir la propri&#233;t&#233; ProtectionLevel
Vous pouvez définir le niveau de protection en appliquant un attribut approprié et en définissant la propriété.Vous pouvez définir la protection au niveau du service afin d'affecter toutes les parties de chaque message, ou vous pouvez la définir à des niveaux de plus en plus spécifiques, des méthodes aux parties du message.[!INCLUDE[crabout](../../../includes/crabout-md.md)] la propriété `ProtectionLevel`, consultez [Fonctionnement des niveaux de protection](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Vous pouvez définir des niveaux de protection dans le code uniquement, mais pas dans la configuration.  
  
### Pour signer tous les messages d'un service  
  
1.  Créez une interface pour le service.  
  
2.  Appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> au service et affectez <xref:System.Net.Security.ProtectionLevel> à la propriété <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A>, tel qu'indiqué dans le code suivant \(le niveau par défaut est <xref:System.Net.Security.ProtectionLevel>\).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### Pour signer toutes les parties de message d'une opération  
  
1.  Créez une interface pour le service et appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à celle\-ci.  
  
2.  Ajoutez une déclaration de méthode à l'interface.  
  
3.  Appliquez l'attribut <xref:System.ServiceModel.OperationContractAttribute> à la méthode et affectez <xref:System.Net.Security.ProtectionLevel> à la propriété <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A>, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## Protection des messages d'erreur  
 Les exceptions levées sur un service peuvent être envoyées à un client en tant qu'erreurs SOAP.[!INCLUDE[crabout](../../../includes/crabout-md.md)] la création d'erreurs fortement typées, consultez [Spécification et gestion des erreurs dans les contrats et les services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) et [Comment : déclarer des erreurs dans des contrats de service](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### Pour protéger un message d'erreur  
  
1.  Créez un type qui représente le message d'erreur.L'exemple suivant crée une classe appelée `MathFault` contenant deux champs.  
  
2.  Appliquez l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> au type et un attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque champ qui doit être sérialisé, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  Dans l'interface qui retournera l'erreur, appliquez l'attribut <xref:System.ServiceModel.FaultContractAttribute> à la méthode que retournera l'erreur et affectez le type de la classe d'erreur au paramètre `detailType`.  
  
4.  Également dans le constructeur, affectez <xref:System.Net.Security.ProtectionLevel> à la propriété <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A>, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## Protection de parties de message  
 Utilisez un contrat de message pour protéger des parties d'un message.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les contrats de message, consultez [Utilisation de contrats de message](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### Pour protéger le corps d'un message  
  
1.  Créez un type qui représente le message.L'exemple suivant crée une classe `Company` contenant deux champs, `CompanyName` et `CompanyID`.  
  
2.  Appliquez l'attribut <xref:System.ServiceModel.MessageContractAttribute> à la classe et affectez <xref:System.Net.Security.ProtectionLevel> à la propriété <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A>.  
  
3.  Appliquez l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> à un champ qui sera exprimé sous forme d'un en\-tête de message et affectez <xref:System.Net.Security.ProtectionLevel> à la propriété `ProtectionLevel`.  
  
4.  Appliquez l'objet <xref:System.ServiceModel.MessageBodyMemberAttribute> aux champs qui seront exprimés sous la forme du corps du message et affectez <xref:System.Net.Security.ProtectionLevel> à la propriété `ProtectionLevel`, tel qu'indiqué dans l'exemple suivant.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## Exemple  
 L'exemple suivant définit la propriété `ProtectionLevel` de plusieurs classes d'attributs à divers emplacements dans un service.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## Compilation du code  
 Le code suivant présente les espaces de noms requis pour compiler l'exemple de code.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>   
 <xref:System.ServiceModel.FaultContractAttribute>   
 <xref:System.ServiceModel.MessageContractAttribute>   
 <xref:System.ServiceModel.MessageBodyMemberAttribute>   
 [Fonctionnement des niveaux de protection](../../../docs/framework/wcf/understanding-protection-level.md)