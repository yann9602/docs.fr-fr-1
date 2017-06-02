---
title: "Utilisation d&#39;assemblys et du Global Assembly Cache | Microsoft Docs"
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
  - "listes de contrôle d'accès (.NET Framework)"
  - "ACL (.NET Framework)"
  - "assemblys (.NET Framework), Global Assembly Cache"
  - "Global Assembly Cache (GAC), avantages"
  - "Global Assembly Cache, avantages"
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Utilisation d&#39;assemblys et du Global Assembly Cache
Si vous comptez partager un assembly entre plusieurs applications, vous pouvez l'installer dans le Global Assembly Cache.  Chaque ordinateur sur lequel le Common Language Runtime est installé possède ce cache de code.  Le Global Assembly Cache stocke les assemblys spécialement destinés à être partagés entre plusieurs applications sur l'ordinateur.  Un assembly doit avoir un nom fort pour être installé dans le Global Assembly Cache.  
  
> [!NOTE]
>  Les assemblys placés dans le Global Assembly Cache doivent avoir le même nom d'assembly et le même nom de fichier \(hormis l'extension de nom de fichier\).  Par exemple, un assembly avec le nom d'assembly myAssembly doit avoir le nom de fichier myAssembly.exe ou myAssembly.dll.  
  
 Vous devez partager des assemblys en les installant dans le Global Assembly Cache uniquement lorsque cela est nécessaire.  En règle générale, maintenez les dépendances d'assembly privées et localisez les assemblys dans le répertoire de l'application, sauf si le partage d'un assembly est explicitement requis.  En outre, vous n'avez pas besoin d'installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.  
  
 Il est possible d'installer un assembly dans le Global Assembly Cache pour plusieurs raisons :  
  
-   Emplacement partagé.  
  
     Les assemblys qui doivent être utilisés par les applications peuvent être placés dans le Global Assembly Cache.  Par exemple, si toutes les applications doivent utiliser un assembly placé dans le Global Assembly Cache, une instruction de stratégie de version peut être ajoutée au fichier Machine.config pour rediriger les références vers l'assembly.  
  
-   Sécurité des fichiers.  
  
     Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d'accès \(ACL, Access Control List\) pour contrôler l'accès en écriture et en exécution.  Le Global Assembly Cache étant installé dans le répertoire systemroot, il hérite de la liste de contrôle d'accès de ce répertoire.  Il est recommandé que seuls les utilisateurs disposant de privilèges d'administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.  
  
-   Versioning côte à côte.  
  
     Plusieurs copies des assemblys ayant le même nom, mais avec des informations de version différentes peuvent être conservées dans le Global Assembly Cache.  
  
-   Emplacement de recherche supplémentaire.  
  
     Le Common Language Runtime vérifie dans le Global Assembly Cache s'il existe un assembly correspondant à l'assembly demandé avant de tester ou d'utiliser les informations du code base dans un fichier de configuration.  
  
 Notez qu'il existe des scénarios au cours desquels vous ne souhaitez explicitement pas installer un assembly dans le Global Assembly Cache.  Si vous placez l'un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ou installer l'application en utilisant XCOPY pour copier le répertoire de l'application.  Dans ce cas, vous devez également déplacer l'assembly dans le Global Assembly Cache.  
  
## Dans cette section  
 [Comment : installer un assembly dans le Global Assembly Cache](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 Décrit les façons d'installer un assembly dans le Global Assembly Cache.  
  
 [Comment : visualiser le contenu du Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 Explique comment utiliser [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour afficher le contenu du Global Assembly Cache.  
  
 [Comment : supprimer un assembly du Global Assembly Cache](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 Explique comment utiliser [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour supprimer un assembly du Global Assembly Cache.  
  
 [Utilisation de composants de service avec le Global Assembly Cache](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 Explique pourquoi les composants pris en charge \(composants COM\+ managés\) doivent être placés dans le Global Assembly Cache.  
  
## Rubriques connexes  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)  
 Fournit une vue d'ensemble de la création d'assemblys.  
  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 Décrit le Global Assembly Cache.  
  
 [Comment : afficher le contenu d'un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Explique comment utiliser [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour afficher les informations de langage MSIL \(Microsoft Intermediate Language\) dans un assembly.  
  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Décrit comment le Common Language Runtime recherche et charge les assemblys qui composent votre application.  
  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Décrit les assemblys, blocs de construction des applications managées.