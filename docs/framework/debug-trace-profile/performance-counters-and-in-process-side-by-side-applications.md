---
title: "Performance Counters and In-Process Side-By-Side Applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "performance counters"
  - "performance counters,and in-process side-by-side applications"
  - "performance,.NET Framework applications"
  - "performance monitoring,counters"
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# Performance Counters and In-Process Side-By-Side Applications
À l'aide de l'analyseur de performances \(Perfmon.exe\), il est possible de différencier les compteurs de performance pour chaque runtime.  Cette rubrique décrit la modification du Registre nécessaire pour activer ces fonctionnalités.  
  
## Comportement par défaut.  
 Par défaut, l'analyseur de performances affiche les compteurs de performance pour chaque application.  Toutefois, ceci pose problème dans deux scénarios :  
  
-   Lorsque vous contrôlez deux applications qui ont le même nom.  Par exemple, si les deux applications sont nommées myapp.exe, l'une apparaîtra sous le nom **myapp** et l'autre sous le nom **myapp\#1** dans la colonne **Instance**.  Dans ce cas, il est difficile de faire correspondre un compteur de performance à une application spécifique.  Vous ne saurez pas si les données collectées pour **myapp\#1** concernent la première ou la seconde application myapp.exe.  
  
-   Lorsqu'une application utilise plusieurs instances du Common Language Runtime.  Le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] prend en charge les scénarios d'hébergement côte à côte in\-process, c'est\-à\-dire qu'un processus ou une application unique peut charger plusieurs instances du Common Language Runtime.  Si une application unique nommée myapp.exe charge deux instances d'exécution, elles seront désignées par défaut dans la colonne **Instance** comme suit : **myapp** et **myapp\#1**.  Dans ce cas, il n'est pas évident de savoir si **myapp** et **myapp\#1** font référence à deux applications portant le même nom ou à la même application avec deux runtimes.  Si plusieurs applications avec le même nom chargent plusieurs runtimes, l'ambiguïté est encore plus grande.  
  
 Vous pouvez définir une clé de Registre pour éliminer cette ambiguïté.  Pour les applications développées à l'aide du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], cette modification du Registre ajoute un identificateur de processus suivi d'un identificateur d'instance d'exécution au nom d'application dans la colonne **Instance**.  Au lieu de *application* ou de *application*\#1, l'application est maintenant identifiée comme code`p`*processID*\_ *application*`r`*runtimeID* dans la colonne **Instance**.  Si une application a été développée à l'aide d'une version antérieure du Common Language Runtime, cette instance est identifiée comme *application\_*`p`*processID*, à condition que le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] soit installé.  
  
## Compteurs de performance pour les applications côte à côte in\-process  
 Pour gérer les compteurs de performance pour plusieurs versions du Common Language Runtime hébergées dans une application unique, vous devez modifier un paramètre de clé de Registre unique, comme indiqué dans la table suivante.  
  
|||  
|-|-|  
|Nom de la clé|HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\.NETFramework\\Performance|  
|Nom de la valeur|ProcessNameFormat|  
|Type valeur|REG\_DWORD|  
|Valeur|1 \(0x00000001\)|  
  
 Une valeur de 0 pour `ProcessNameFormat` indique que le comportement par défaut est activé, c'est\-à\-dire que Perfmon.exe affiche des compteurs de performance pour chaque application.  Lorsque vous affectez la valeur 1, Perfmon.exe supprime l'ambiguïté de plusieurs versions d'une application et fournit des compteurs de performance pour chaque exécution.  Toute valeur autre que `ProcessNameFormat` pour le paramètre de clé de Registre n'est pas prise en charge et réservée pour une utilisation future.  
  
 Après avoir mis à jour le paramètre de clé de Registre `ProcessNameFormat`, vous devez redémarrer Perfmon.exe, ou tout autre consommateur de compteurs de performance, afin que la nouvelle fonctionnalité d'attribution de nom d'instance fonctionne correctement.  
  
 L'exemple suivant indique comment modifier la valeur `ProcessNameFormat` par programmation.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Lorsque vous effectuez cette modification du Registre, Perfmon.exe affiche les noms des applications qui visent le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] comme *application*\_`p`*processID*\_`r`*runtimeID*, où application *application* est le nom de l'application, *processID* l'identificateur de processus de l'application et *runtimeID* un identificateur du Common Language Runtime.  Par exemple, si une application nommée myapp.exe charge deux instances du Common Language Runtime, Perfmon.exe peut identifier une instance comme myapp\_p1416\_r10 et la seconde comme myapp\_p3160\_r10.  L'identificateur d'exécution ne fait que lever l'ambiguïté sur les runtimes dans un processus ; il ne fournit pas d'autres informations sur le runtime. \(Par exemple, l'ID d'exécution n'a aucune relation avec la version ou la référence du runtime.\)  
  
 Si le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] est installé, la modification du Registre affecte également les applications développées à l'aide de versions antérieures du .NET Framework.  Celles\-ci apparaissent dans Perfmon.exe comme *application\_*`p`*processID*, où *application* est le nom de l'application et *processID* l'identificateur de processus.  Par exemple, si les compteurs de performance de deux applications nommées myapp.exe sont contrôlés, l'un peut apparaître comme myapp\_p23900 et l'autre comme myapp\_p24908.  
  
> [!NOTE]
>  L'identificateur de processus élimine l'ambiguïté de la résolution de deux applications avec le même nom qui utilisent des versions antérieures du runtime.  Un identificateur d'exécution n'est pas nécessaire pour les versions antérieures, car les versions antérieures du Common Language Runtime ne prennent pas en charge les scénarios côte à côte.  
  
 Si le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] n'est pas présent ou a été désinstallé, la définition de la clé de Registre n'a aucun effet.  Cela signifie que deux applications avec le même nom continueront à apparaître dans Perfmon.exe comme *application* et *application\#1* \(par exemple, **myapp** et **myapp\#1**\).