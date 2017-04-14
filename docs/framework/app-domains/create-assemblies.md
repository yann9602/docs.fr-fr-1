---
title: "Cr&#233;ation d&#39;assemblys | Microsoft Docs"
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
  - "assemblys (.NET Framework), créer"
  - "assemblys (.NET Framework), multifichiers"
  - "assemblys multifichiers"
  - "assemblys à fichier unique"
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Cr&#233;ation d&#39;assemblys
Vous pouvez créer des assemblys à fichier unique ou multifichiers à l'aide d'un IDE, tel que [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], ou les compilateurs et outils fournis par le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  L'assembly le plus simple est un fichier unique ayant un nom simple et qui est chargé dans un seul domaine d'application.  Cet assembly ne peut pas être référencé par d'autres assemblys en dehors du répertoire de l'application et ne peut pas passer la vérification de la version.  Pour désinstaller l'application composée de l'assembly, vous supprimez simplement le répertoire dans lequel elle réside.  Pour de nombreux développeurs, un assembly disposant de ces fonctionnalités représente le seul élément nécessaire pour déployer une application.  
  
 Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et de fichiers de ressources.  Vous pouvez également créer un assembly pouvant être partagé par plusieurs applications.  Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.  
  
 Lorsque vous regroupez des ressources et des modules de code dans des assemblys, vous disposez de plusieurs options, en fonction des facteurs suivants :  
  
-   Versioning  
  
     Regroupe des modules qui doivent avoir les mêmes informations de version.  
  
-   Déploiement  
  
     Regroupe les modules de code et les ressources prenant en charge votre modèle de déploiement.  
  
-   Réutilisation  
  
     Regroupe les modules pouvant être logiquement utilisés ensemble à des fins particulières.  Par exemple, un assembly composé de types et de classes peu utilisées pour la maintenance du programme peut être placé dans le même assembly simple.  De plus, les types que vous souhaitez partager entre plusieurs applications doivent être regroupés dans un assembly. Cet assembly doit être signé avec un nom fort.  
  
-   Sécurité  
  
     Regroupe les modules contenant des types requérant les mêmes autorisations de sécurité.  
  
-   Portée  
  
     Regroupe les modules contenant des types dont la visibilité doit être limitée à l'assembly.  
  
 Des considérations particulières doivent être prises en compte lors de la mise à la disposition d'assemblys du Common Language Runtime à des applications COM non managées.  Pour plus d'informations sur l'utilisation de codes non managés, consultez [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).  
  
## Voir aussi  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [Versioning des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)   
 [Comment : générer un assembly à fichier unique](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)   
 [Comment : générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)