---
title: "Comment&#160;: configurer un domaine d&#39;application | Microsoft Docs"
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
  - "domaines d'application, configurer"
  - "ApplicationBase (propriété)"
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: configurer un domaine d&#39;application
Vous pouvez fournir au Common Language Runtime des informations de configuration pour un nouveau domaine d'application à l'aide de la classe <xref:System.AppDomainSetup>.  Lorsque vous créez vos propres domaines d'application, la propriété la plus importante est <xref:System.AppDomainSetup.ApplicationBase%2A>.  Les autres propriétés **AppDomainSetup** sont principalement utilisées par les hôtes de runtime pour configurer un domaine d'application.  
  
 La propriété **ApplicationBase** définit le répertoire racine de l'application.  Lorsque le runtime a besoin de satisfaire une demande de type, il teste l'assembly contenant le type dans le répertoire spécifié par la propriété **ApplicationBase**.  
  
> [!NOTE]
>  Un nouveau domaine d'application n'hérite que de la propriété **ApplicationBase** du créateur.  
  
 L'exemple suivant crée une instance de la classe **AppDomainSetup**, utilise cette classe pour créer un domaine d'application, écrit les informations dans la console, puis décharge le domaine d'application.  
  
## Exemple  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## Voir aussi  
 [Hosting Overview](http://msdn.microsoft.com/fr-fr/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)