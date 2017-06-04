---
title: "Comment&#160;: cr&#233;er un contrat de donn&#233;es de base destin&#233; &#224; une classe ou une structure | Microsoft Docs"
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
helpviewer_keywords: 
  - "contrats de données (WCF), création pour une classe ou une structure"
  - "classe DataContractAttribute"
  - "DataMemberAttribute"
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# Comment&#160;: cr&#233;er un contrat de donn&#233;es de base destin&#233; &#224; une classe ou une structure
Cette rubrique illustre les étapes de base pour créer un contrat de données à l'aide d'une classe ou d'une structure.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les contrats de données et leur utilisation, consultez [Utilisation de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Pour consulter le didacticiel sur les étapes de la création d'un service et d'un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de base, consultez [Didacticiel de mise en route](../../../../docs/framework/wcf/getting-started-tutorial.md).  Pour obtenir un exemple d'application fonctionnel qui se compose d'un service et d'un client simples, consultez [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### Pour créer un contrat de données de base destiné à une classe ou une structure  
  
1.  Déclarez que le type a un contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.  Notez que tous les types publics, y compris ceux sans attributs, sont sérialisables.  Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est absent.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], consultez [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Définissez les membres \(propriétés, champs ou événements\) sérialisés en appliquant l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque membre.  Ces membres sont appelés des membres de données.  Par défaut, tous les types publics sont sérialisables.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], consultez [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux champs privés, ce qui expose les données aux autres.  Vérifiez que le membre ne contient pas de données sensibles.  
  
## Exemple  
 L'exemple suivant montre comment créer un contrat de données pour le type `Person` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [Utilisation de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)   
 [Didacticiel de mise en route](../../../../docs/framework/wcf/getting-started-tutorial.md)   
 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)