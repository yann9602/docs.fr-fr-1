---
title: "Comment&#160;: obtenir des informations relatives au type et aux membres &#224; partir d&#39;un assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), obtenir des informations à partir de"
  - "obtenir des informations sur les assemblys"
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: obtenir des informations relatives au type et aux membres &#224; partir d&#39;un assembly
L'espace de noms <xref:System.Reflection> contient plusieurs méthodes pour obtenir des informations à partir d'un assembly.  Cette section illustre l'une de ces méthodes.  Pour plus d'informations, consultez [Vue d'ensemble de la réflexion](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 L'exemple suivant obtient des informations relatives au type et aux membres à partir d'un assembly.  
  
## Exemple  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## Voir aussi  
 [Hosting Overview](http://msdn.microsoft.com/fr-fr/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)