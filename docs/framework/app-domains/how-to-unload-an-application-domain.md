---
title: "Comment&#160;: d&#233;charger un domaine d&#39;application | Microsoft Docs"
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
  - "Unload (méthode)"
  - "domaines d’application, décharger"
  - "décharger des domaines d'application"
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;charger un domaine d&#39;application
Lorsque vous avez fini d'utiliser un domaine d'application, déchargez\-le à l'aide de la méthode [System.AppDomain.Unload](frlrfSystemAppDomainClassUnloadTopic).  La méthode **Unload** arrête gracieusement le domaine d'application spécifié.  Lors du processus de déchargement, aucun nouveau thread ne peut accéder au domaine d'application et toutes les structures de données spécifiques aux domaines d'application sont libérées.  
  
 Les assemblys chargés dans le domaine d'application sont supprimés et ne sont plus disponibles.  Si un assembly du domaine d'application est indépendant du domaine, les données de l'assembly restent en mémoire jusqu'à l'arrêt de l'ensemble du processus.  Il n'existe pas d'autre mécanisme de déchargement d'un assembly indépendant du domaine que l'arrêt de l'ensemble du processus.  Dans certaines situations, la requête de déchargement d'un domaine d'application ne fonctionne pas et entraîne une <xref:System.CannotUnloadAppDomainException>.  
  
 L'exemple suivant crée un domaine d'application appelé `MyDomain`, imprime certaines informations dans la console, puis décharge le domaine d'application.  Notez que le code tente ensuite d'imprimer le nom convivial du domaine d'application déchargé dans la console.  Cette action génère une exception qui est gérée par les instructions try\/catch à la fin du programme.  
  
## Exemple  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## Voir aussi  
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Comment : créer un domaine d'application](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)