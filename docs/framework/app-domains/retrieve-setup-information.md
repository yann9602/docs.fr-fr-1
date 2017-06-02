---
title: "R&#233;cup&#233;ration d&#39;informations d&#39;installation &#224; partir d&#39;un domaine d&#39;application | Microsoft Docs"
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
  - "AppDomainSetup (objet)"
  - "domaines d'application, récupérer des informations de configuration"
  - "récupérer des informations de configuration"
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# R&#233;cup&#233;ration d&#39;informations d&#39;installation &#224; partir d&#39;un domaine d&#39;application
Chaque instance d'un domaine d'application est composée de propriétés et d'informations <xref:System.AppDomainSetup>.  Vous pouvez récupérer des informations d'installation à partir d'un domaine d'application à l'aide de la classe <xref:System.AppDomain?displayProperty=fullName>.  Cette classe fournit plusieurs membres qui récupèrent les informations de configuration sur un domaine d'application.  
  
 Vous pouvez également interroger l'objet **AppDomainSetup** pour le domaine d'application, afin d'obtenir des informations d'installation passées au domaine lors de sa création.  
  
 L'exemple suivant crée un domaine d'application, puis imprime plusieurs valeurs de membre dans la console.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 L'exemple suivant définit, puis récupère les informations d'installation pour un domaine d'application.  Notez que `AppDomain.SetupInformation.ApplicationBase` obtient les informations de configuration.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## Voir aussi  
 [Hosting Overview](http://msdn.microsoft.com/fr-fr/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)