---
title: "Caching in .NET Framework Applications | Microsoft Docs"
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
  - "ASP.NET caching"
  - "caching [.NET Framework]"
  - "caching [ASP.NET]"
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
caps.latest.revision: 26
author: "tdykstra"
ms.author: "tdykstra"
manager: "wpickett"
caps.handback.revision: 26
---
# Caching in .NET Framework Applications
La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement.  Lors d'un nouvel accès aux données, les applications peuvent les obtenir du cache au lieu de les extraire de la source d'origine.  Cela peut améliorer le niveau de performance et l'extensibilité.  En outre, la mise en cache rend les données disponibles lorsque la source de données est temporairement indisponible.  
  
 Le .NET Framework fournit des fonctionnalités de mise en cache que vous pouvez utiliser pour améliorer le niveau de performance et l'extensibilité du client Windows et des applications serveur, notamment ASP.NET.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et versions antérieures, ASP.NET fournissait une implémentation de cache en mémoire dans l'espace de noms <xref:System.Web.Caching>.  Dans les versions précédentes du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], la mise en cache était disponible uniquement dans l'espace de noms <xref:System.Web> et nécessitait donc une dépendance sur les classes ASP.NET.  Dans .NET Framework 4, l'espace de noms <xref:System.Runtime.Caching> contient des API conçues pour les applications Web et non Web.  
  
## Mise en cache des données  
 Vous pouvez mettre en cache les informations à l'aide de classes dans l'espace de noms <xref:System.Runtime.Caching>.  Les classes de mise en cache dans cet espace de noms fournissent les fonctionnalités suivantes :  
  
-   Les types abstraits qui fournissent la base de la création d'implémentations de cache personnalisées.  
  
-   Une implémentation de cache d'objets en mémoire concrète.  
  
 La classe de base abstraite de mise en cache \(<xref:System.Runtime.Caching.ObjectCache>\) définit les tâches de mise en cache suivantes :  
  
-   Création et gestion des entrées de cache.  
  
-   Spécification des informations d'expiration et d'éviction.  
  
-   Déclenchement des événements en réponse à des modifications apportées aux entrées du cache.  
  
 La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation de cache d'objets en mémoire de la classe <xref:System.Runtime.Caching.ObjectCache>.  Vous pouvez utiliser la classe <xref:System.Runtime.Caching.MemoryCache> pour la plupart des tâches de mise en cache.  
  
> [!NOTE]
>  La classe <xref:System.Runtime.Caching.MemoryCache> est modélisée sur l'objet de cache ASP.NET qui est défini dans l'espace de noms <xref:System.Web.Caching>.  Par conséquent, la logique interne de mise en cache est similaire à la logique fournie dans les versions antérieures d'ASP.NET.  
  
 Pour obtenir un exemple d'utilisation de la mise en cache dans une application WPF, consultez [Procédure pas à pas : mise en cache de données d'application dans une application WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## Mise en cache dans les applications ASP.NET  
 Les classes de mise en cache dans l'espace de noms <xref:System.Runtime.Caching> fournissent des fonctionnalités de mise en cache des données dans ASP.NET.  
  
> [!NOTE]
>  Si votre application cible le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ou une version antérieure, vous devez utiliser les classes de mise en cache qui sont définies dans l'espace de noms <xref:System.Web.Caching>.  Pour plus d'informations, consultez [ASP.NET Caching Overview](../Topic/ASP.NET%20Caching%20Overview.md).  
  
> [!NOTE]
>  Lorsque vous développez des applications, nous vous recommandons d'utiliser la classe <xref:System.Runtime.Caching.MemoryCache>.  L'API qui est fournie dans l'espace de noms <xref:System.Runtime.Caching> est semblable à l'API fournie dans l'espace de noms <xref:System.Web.Caching.Cache>.  Par conséquent, l'API vous sera familière si vous avez utilisé la mise en cache dans les versions antérieures d'ASP.NET. Pour obtenir un exemple d'utilisation de la mise en cache dans les applications ASP.NET, consultez [Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md).  
  
### Mise en cache de sortie  
 Pour mettre manuellement en cache des données d'applications, vous pouvez utiliser la classe <xref:System.Runtime.Caching.MemoryCache> dans ASP.NET. ASP.NET prend également en charge la mise en cache de sortie, qui stocke la sortie de pages générée, les contrôles et les réponses HTTP en mémoire.  Vous pouvez configurer la mise en cache de sortie de façon déclarative dans une page Web ASP.NET ou à l'aide des paramètres du fichier Web.config.  Pour plus d'informations, consultez [outputCache, élément de caching \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 ASP.NET vous permet d'étendre la mise en cache de sortie en créant des fournisseurs de cache de sortie personnalisés.  À l'aide de fournisseurs personnalisés, vous pouvez stocker le contenu mis en cache avec d'autres dispositifs de stockage tels que les disques, le stockage en nuage et les moteurs de cache distribués.  Pour créer un fournisseur de cache de sortie personnalisé, vous créez une classe qui dérive de la classe <xref:System.Web.Caching.OutputCacheProvider> et configurez l'application pour utiliser le fournisseur du cache de sortie personnalisé.  
  
## Mise en cache dans les services WCF REST  
 Pour les services WCF REST, le .NET Framework vous permet de tirer parti de la mise en cache de sortie déclarative qui est disponible dans ASP.NET. Cela vous permet de mettre en cache les réponses provenant de vos opérations de service WCF REST.  Lorsqu'un utilisateur envoie une requête HTTP GET à un service qui est configuré pour la mise en cache, ASP.NET renvoie la réponse mise en cache et la méthode de service n'est pas appelée.  Une fois que le cache expire, la prochaine fois qu'un utilisateur envoie une requête HTTP GET, votre méthode de service est appelée et la réponse est de nouveau la mise en cache.  
  
 Le .NET Framework vous permet également d'implémenter une mise en cache HTTP GET conditionnelle.  Dans les scénarios REST, une requête HTTP GET conditionnelle est souvent utilisée par les services pour implémenter la mise en cache HTTP intelligente, comme décrit dans les [Spécifications HTTP \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=165800).  Pour plus d'informations, consultez [Mettre en cache la prise en charge des services Web WCF HTTP](http://go.microsoft.com/fwlink/?LinkId=184598).  
  
## Extension de la mise en cache dans le .NET Framework  
 La mise en cache dans le .NET Framework est conçue pour être extensible.  La classe <xref:System.Runtime.Caching.ObjectCache> vous permet de créer une implémentation de cache personnalisée.  Cette classe fournit des membres qui sont disponibles pour toutes les applications managées, notamment Windows Forms, Windows Presentation Foundation \(WPF\) et Windows Communications Foundation \(WCF\).  Vous pouvez effectuer cette opération afin de créer une classe de cache qui utilise un mécanisme de stockage différent ou si vous souhaitez avoir un contrôle précis des opérations de cache.  
  
 Pour étendre la mise en cache, vous pouvez effectuer les opérations suivantes :  
  
-   Créez une classe personnalisée qui dérive de la classe <xref:System.Runtime.Caching.ObjectCache> puis fournissez une implémentation de cache personnalisée dans la classe dérivée.  
  
-   Créez une classe qui dérive de la classe <xref:System.Runtime.Caching.MemoryCache> et personnalisez ou étendez la classe dérivée.  Pour obtenir un exemple de cette procédure, consultez [Données d'application de mise en cache à l'aide de plusieurs objets cache dans une application ASP .NET.](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Créez une classe qui dérive de la classe <xref:System.Web.Caching.OutputCacheProvider> et configurez l'application pour utiliser le fournisseur du cache de sortie personnalisé.  
  
 Pour plus d'informations, consultez l'entrée [Mise en cache de sortie extensible avec ASP.NET 4 \(séries VS 2010 et .NET 4.0\) \(éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=185772) du blog de Scott Guthrie.  
  
## Voir aussi  
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching.MemoryCache>   
 [Procédure pas à pas : mise en cache de données d'application dans une application WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)   
 [Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md)