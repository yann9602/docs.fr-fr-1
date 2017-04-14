---
title: "Comment&#160;: supprimer un assembly du Global Assembly Cache | Microsoft Docs"
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
  - "assemblys (.NET Framework), Global Assembly Cache"
  - "supprimer des assemblys du Global Assembly Cache"
  - "Global Assembly Cache (GAC), supprimer les assemblys"
  - "Gacutil.exe"
  - "Global Assembly Cache (outil)"
  - "Global Assembly Cache, supprimer les assemblys"
  - "supprimer des assemblys du Global Assembly Cache"
  - "assemblys avec nom fort, Global Assembly Cache"
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: supprimer un assembly du Global Assembly Cache
Il existe deux façons de supprimer un assembly du Global Assembly Cache \(GAC\) :  
  
-   En utilisant l'[outil Global Assembly Cache \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  Vous pouvez utiliser cette option pour désinstaller des assemblys que vous avez placés dans le GAC lors du développement et des tests.  
  
-   En utilisant [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).  Utilisez cette option pour désinstaller des assemblys quand vous testez des packages d'installation et pour les systèmes de production.  
  
### Suppression d'un assembly avec Gacutil.exe  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     **gacutil \-i** \<*nom de l'assembly*\>  
  
     Dans cette commande, *nom de l'assembly* est le nom de l'assembly à supprimer du Global Assembly Cache.  
  
    > [!WARNING]
    >  Vous ne devez pas utiliser Gacutil.exe pour supprimer des assemblys sur des systèmes de production, en raison de la possibilité que l'assembly soit encore requis par certaines applications.  Au lieu de cela, vous devez utiliser Windows Installer, qui conserve un comptage des références pour chaque assembly qu'il installe dans le GAC.  
  
 L'exemple suivant supprime un assembly nommé `hello.dll` du Global Assembly Cache.  
  
```  
gacutil -u hello  
```  
  
### Suppression d'un assembly avec Windows Installer  
  
1.  Dans l'application **Programmes et fonctionnalités**, dans le **Panneau de configuration**, sélectionnez l'application que vous voulez désinstaller.  Si le package d'installation a placé les assemblys dans le GAC, Windows Installer les supprime s'ils ne sont pas utilisés par une autre application.  
  
    > [!NOTE]
    >  Windows Installer conserve un comptage des références pour les assemblys installés dans le GAC.  Un assembly est supprimé du GAC seulement quand son comptage des références atteint zéro, ce qui indique qu'il n'est utilisé par aucune application installée par un package Windows Installer.  
  
## Voir aussi  
 [Utilisation d'assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Comment : installer un assembly dans le Global Assembly Cache](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)