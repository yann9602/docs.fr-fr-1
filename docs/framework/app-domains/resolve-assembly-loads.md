---
title: "R&#233;solution des chargements d&#39;assemblys | Microsoft Docs"
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
  - "assemblys (.NET Framework), résoudre les chargements"
  - "domaines d’application, chargement d’assemblys"
  - "résoudre les chargements d'assemblys"
  - "assemblys (.NET Framework), chargement"
  - "domaines d’application, résolution des chargements d’assemblys"
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# R&#233;solution des chargements d&#39;assemblys
Le .NET Framework fournit l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> pour les applications qui requièrent un meilleur contrôle du chargement d'assembly.  En gérant cet événement, votre application peut charger un assembly dans le contexte de chargement depuis l'extérieur des chemins d'accès de détection normaux, sélectionner la version d'assembly à charger parmi plusieurs, émettre un assembly dynamique et le retourner, et ainsi de suite.  Cette rubrique fournit des instructions pour la gestion de l'événement <xref:System.AppDomain.AssemblyResolve>.  
  
> [!NOTE]
>  Pour résoudre les chargements d'assemblys dans le contexte ReflectionOnly, utilisez l'événement <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=fullName> à la place.  
  
## Fonctionnement de l'événement AssemblyResolve  
 Lorsque vous enregistrez un gestionnaire pour l'événement <xref:System.AppDomain.AssemblyResolve>, le gestionnaire est appelé chaque fois que le runtime ne peut pas lier un assembly par nom.  Par exemple, l'appel des méthodes suivantes à partir du code utilisateur peut provoquer le déclenchement de l'événement <xref:System.AppDomain.AssemblyResolve> :  
  
-   Une surcharge de la méthode <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> dont le premier argument est une chaîne qui représente le nom complet de l'assembly à charger \(c'est\-à\-dire, la chaîne retournée par la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName>\).  
  
-   Une surcharge de la méthode <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> dont le premier argument est un objet <xref:System.Reflection.AssemblyName> qui identifie l'assembly à charger.  
  
-   Une surcharge de méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>.  
  
-   Une surcharge de méthode <xref:System.AppDomain.CreateInstance%2A?displayProperty=fullName> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName> qui instancie un objet dans un autre domaine d'application.  
  
### Opérations effectuées par le gestionnaire d'événements  
 Le gestionnaire de l'événement <xref:System.AppDomain.AssemblyResolve> reçoit le nom complet de l'assembly à charger dans la propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName>.  Si le gestionnaire ne reconnaît pas le nom de l'assembly, il retourne null \(`Nothing` dans Visual Basic, `nullptr` dans Visual C\+\+\).  
  
 Si le gestionnaire reconnaît le nom de l'assembly, il peut charger et retourner un assembly qui satisfait la requête.  La liste suivante décrit certains scénarios d'exemple.  
  
-   Si le gestionnaire connaît l'emplacement d'une version de l'assembly, il peut charger ce dernier à l'aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> et retourner l'assembly chargé si l'opération a réussi.  
  
-   Si le gestionnaire a accès à une base de données à partir d'assemblys stockés sous forme de tableaux d'octets, il peut charger un tableau d'octets à l'aide de l'une des surcharges de méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> qui prennent un tableau d'octets.  
  
-   Le gestionnaire peut générer un assembly dynamique et le retourner.  
  
> [!NOTE]
>  Le gestionnaire doit charger l'assembly dans le contexte LoadFrom, dans le contexte de chargement, ou sans contexte.  Si le gestionnaire charge l'assembly dans le contexte ReflectionOnly en utilisant la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=fullName>, la tentative de chargement qui a déclenché l'événement <xref:System.AppDomain.AssemblyResolve> échoue.  
  
 Il est de la responsabilité du gestionnaire d'événements de retourner un assembly approprié.  Le gestionnaire peut analyser le nom complet de l'assembly demandé en passant la valeur de propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> au constructeur <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.  En commençant par [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], le gestionnaire peut utiliser la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> pour déterminer si la requête actuelle est une dépendance d'un autre assembly.  Ces informations peuvent aider à identifier un assembly qui satisfera la dépendance.  
  
 Le gestionnaire d'événements peut retourner une version de l'assembly différente de celle qui a été demandée.  
  
 Dans la plupart des cas, l'assembly qui est retourné par le gestionnaire apparaît dans le contexte de chargement, indépendamment du contexte dans lequel le gestionnaire le charge.  Par exemple, si le gestionnaire utilise la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> pour charger un assembly dans le contexte LoadFrom, l'assembly apparaît dans le contexte de chargement lorsque le gestionnaire le retourne.  Toutefois, dans le cas suivant, l'assembly apparaît sans contexte lorsque le gestionnaire le retourne :  
  
-   Le gestionnaire charge un assembly sans contexte.  
  
-   La propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> n'a pas la valeur null.  
  
-   L'assembly demandeur \(c'est\-à\-dire, l'assembly qui est retourné par la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName>\) a été chargé sans contexte.  
  
 Pour plus d'informations sur les contextes, consultez la surcharge de la méthode <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=fullName>.  
  
 Plusieurs versions du même assembly peuvent être chargées dans le même domaine d'application.  Cette pratique n'est pas recommandée, car elle peut entraîner des problèmes d'assignation de type.  Consultez [Meilleures pratiques pour le chargement d'assembly](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### Ce que le gestionnaire d'événements ne doit pas faire  
 La règle principale pour gérer l'événement <xref:System.AppDomain.AssemblyResolve> est que vous ne devez pas essayer de retourner un assembly que vous ne reconnaissez pas.  Lorsque vous écrivez le gestionnaire, vous devez savoir quels assemblys peuvent provoquer le déclenchement de l'événement.  Votre gestionnaire doit retourner null pour d'autres assemblys.  
  
> [!IMPORTANT]
>  En commençant par [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], l'événement <xref:System.AppDomain.AssemblyResolve> est déclenché pour les assemblys satellites.  Cette modification affecte un gestionnaire d'événements qui a été écrit pour une version antérieure du .NET Framework, si le gestionnaire tente de résoudre toutes les requêtes de chargement d'assembly.  Les gestionnaires d'événements qui ignorent les assemblys qu'ils ne reconnaissent pas ne sont pas affectés par cette modification : Ils retournent la valeur null et les mécanismes de secours normaux sont suivis.  
  
 Lors du chargement d'un assembly, le gestionnaire d'événements ne doit pas utiliser les surcharges de méthode <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> qui peuvent provoquer le déclenchement de l'événement <xref:System.AppDomain.AssemblyResolve> de manière récursive, car cela peut provoquer un dépassement de capacité de la pile. \(Consultez la liste fournie plus haut dans cette rubrique.\) Cela se produit même si vous fournissez la gestion des exceptions pour la demande de chargement, car aucune exception n'est levée jusqu'à ce que tous les gestionnaires d'événements aient été retournés.  Par conséquent, le code suivant provoque un dépassement de capacité de la pile si `MyAssembly` est introuvable :  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## Voir aussi  
 [Meilleures pratiques pour le chargement d'assembly](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)