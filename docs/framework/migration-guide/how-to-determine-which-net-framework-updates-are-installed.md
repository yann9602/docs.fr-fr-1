---
title: "Guide pratique pour déterminer les mises à jour .NET Framework installées | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 6a6e4c9c2bdacc01f82d3a53aec706809bcfaa5a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
<a id="how-to-determine-which-net-framework-updates-are-installed" class="xliff"></a>

# Comment : déterminer les mises à jour .NET Framework installées
Les mises à jour installées pour chaque version du .NET Framework installée sur un ordinateur sont répertoriées dans le Registre Windows. Vous pouvez utiliser l'Éditeur du Registre (regedit.exe) pour afficher ces informations.  
  
 Dans l'Éditeur du Registre, les versions du .NET Framework et les mises à jour installées pour chaque version sont stockées dans des sous-clés distinctes. Pour plus d'informations sur la détection des numéros des versions installées, voir [Comment : déterminer les versions .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Pour plus d’informations sur l’installation du .NET Framework, consultez [Installer le .NET Framework pour les développeurs](../../../docs/framework/install/guide-for-developers.md).  
  
<a id="to-find-installed-updates" class="xliff"></a>

### Pour trouver les mises à jour installées  
  
1.  Ouvrez le programme **regedit.exe**. Dans Windows 8 et les versions ultérieures, ouvrez l'écran d'accueil et tapez le nom. Dans les versions antérieures de Windows, dans le menu **Démarrer**, choisissez **Exécuter** puis, dans la zone **Ouvrir**, entrez **regedit.exe**.  
  
     Vous devez disposer d'informations d'identification d'administration pour exécuter regedit.exe.  
  
2.  Dans l'Éditeur du Registre, ouvrez la sous-clé suivante :  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     Les mises à jour installées sont répertoriées sous les sous-clés qui identifient la version du .NET Framework auquel elles s'appliquent. Chaque mise à jour est identifiée par un numéro de Base de connaissances (KB).  
  
<a id="example" class="xliff"></a>

## Exemple  
 Le code suivant détermine par programmation les mises à jour du .NET Framework installées sur un ordinateur. Vous devez disposer d'informations d'identification d'administration pour exécuter cet exemple.  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 Cet exemple produit un résultat semblable au suivant :  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
<a id="see-also" class="xliff"></a>

## Voir aussi

[Guide pratique pour déterminer les versions .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Installation du .NET Framework](../../../docs/framework/install/guide-for-developers.md)   
[Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)

