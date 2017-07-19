---
title: Global Assembly Cache | Documents Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0a40c6dcc51728bb069381b8af4652ce533bb08c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/02/2017

---
# <a name="global-assembly-cache"></a>Global Assembly Cache
Chaque ordinateur sur lequel le Common Language Runtime est installé a un cache de code à l’échelle de l’ordinateur appelé Global Assembly Cache. Le Global Assembly Cache stocke les assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.  
  
 Vous ne devez partager des assemblys en les installant dans le Global Assembly Cache qu’en cas de nécessité. En règle générale, vous devez maintenir les dépendances d’assembly privées et rechercher les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement requis. En outre, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.  
  
> [!NOTE]
>  Il existe des scénarios où vous ne souhaitez explicitement pas installer un assembly dans le Global Assembly Cache. Si vous placez l’un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant la commande **xcopy** pour copier le répertoire de l’application. Vous devez également déplacer l’assembly dans le Global Assembly Cache.  
  
 Il existe deux manières de déployer un assembly dans le Global Assembly Cache :  
  
-   Utiliser un programme d’installation conçu pour fonctionner avec le Global Assembly Cache. Il s’agit de l’option par défaut d’installation d’assemblys dans le Global Assembly Cache.  
  
-   Utiliser un outil de développement appelé [Outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) fourni avec le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Dans les scénarios de déploiement, utilisez Windows Installer pour installer des assemblys dans le Global Assembly Cache. Utilisez l’outil Global Assembly Cache uniquement dans les scénarios de développement, car il ne propose pas de fonctionnalités de décompte des références d’assembly et d’autres fonctionnalités disponibles lors de l’utilisation de Windows Installer.  
  
 À compter du .NET Framework 4, l’emplacement par défaut du Global Assembly Cache est **%windir%\Microsoft.NET\assembly**. Dans les versions antérieures du .NET Framework, l’emplacement par défaut est **%windir%\assembly**.  
  
 Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution. Le Global Assembly Cache étant installé dans un sous-répertoire du répertoire systemroot, il hérite de la liste de contrôle d’accès de ce répertoire. Il est recommandé que seuls les utilisateurs disposant de privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.  
  
 Les assemblys déployés dans le Global Assembly Cache doivent avoir un nom fort. Quand un assembly est ajouté au Global Assembly Cache, des contrôles d’intégrité sont effectués sur tous les fichiers qui composent l’assembly. Le cache effectue ces contrôles d’intégrité pour vérifier qu’aucun assembly n’a été falsifié, par exemple quand un fichier a changé mais que le manifeste ne reflète pas ce changement.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys dans le common language runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [Utilisation d’assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)
