---
title: "Rappels de s&#233;rialisation avec tol&#233;rance de version | Microsoft Docs"
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
  - "OnDeserializedAttribute [WCF]"
  - "OnDeserializingAttribute [WCF]"
  - "OnSerializedAttribute [WCF]"
  - "OnSerializingAttribute [WCF]"
  - "sérialisation (WCF), définir des valeurs par défaut"
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Rappels de s&#233;rialisation avec tol&#233;rance de version
Le modèle de programmation de contrat de données prend entièrement en charge les méthodes de rappel de sérialisation avec tolérance de version que les classes <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> prennent en charge.  
  
## Attributs avec tolérance de version  
 Il existe quatre attributs de rappel.Chaque attribut peut être appliqué à une méthode que le moteur de sérialisation\/désérialisation appelle à différents moments.Le tableau suivant explique quand utiliser chaque attribut.  
  
|Attribut|Lorsque la méthode correspondante est appelée|  
|--------------|---------------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Appelé avant de sérialiser le type.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Appelé après avoir sérialisé le type.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Appelé avant de désérialiser le type.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Appelé après avoir désérialisé le type.|  
  
 Les méthodes doivent accepter un paramètre <xref:System.Runtime.Serialization.StreamingContext>.  
  
 Ces méthodes sont principalement destinées à une utilisation avec le versioning ou l'initialisation.Pendant la désérialisation, aucun constructeur n'est appelé.Par conséquent, des membres de données risquent de ne pas être initialisés correctement \(avec les valeurs par défaut prévues\) si les données de ces membres ne figurent pas dans le flux entrant, par exemple, si les données viennent d'une version antérieure d'un type auquel il manque certains membres de données.Pour corriger ce problème, utilisez la méthode de rappel marquée avec <xref:System.Runtime.Serialization.OnDeserializingAttribute>, comme indiqué dans l'exemple suivant.  
  
 Vous pouvez marquer uniquement une méthode par type avec chacun des attributs de rappel précédents.  
  
### Exemple  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>   
 <xref:System.Runtime.Serialization.OnSerializedAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>   
 <xref:System.Runtime.Serialization.StreamingContext>   
 [Sérialisation avec tolérance de version](../../../../docs/framework/serialization/version-tolerant-serialization.md)