---
title: "Comment&#160;: cr&#233;er un domaine d&#39;application | Microsoft Docs"
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
  - "domaines d’application, création"
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un domaine d&#39;application
Un hôte Common Language Runtime crée automatiquement des domaines d'application lorsqu'ils sont nécessaires.  Toutefois, vous pouvez créer vos propres domaines d'application et y charger les assemblys que vous souhaitez gérer personnellement.  Vous pouvez également créer des domaines d'application à partir desquels exécuter le code.  
  
 Vous créez un domaine d'application à l'aide de l'une des méthodes **CreateDomain** surchargées de la classe <xref:System.AppDomain?displayProperty=fullName>.  Vous pouvez attribuer un nom au domaine d'application et le référencer par ce nom.  
  
 L'exemple suivant crée un domaine d'application, lui assigne le nom `MyDomain`, puis imprime le nom du domaine hôte et du domaine d'application enfant créé dans la console.  
  
## Exemple  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## Voir aussi  
 [Hosting Overview](http://msdn.microsoft.com/fr-fr/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)