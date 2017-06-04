---
title: "Global Assembly Cache | Microsoft Docs"
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
  - "cache (.NET Framework), Global Assembly Cache"
  - "Global Assembly Cache (GAC)"
  - "Global Assembly Cache"
  - "Global Assembly Cache, à propos de"
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Global Assembly Cache
Chaque ordinateur sur lequel le Common Language Runtime est installé possède un cache de code à l'échelle de l'ordinateur appelé Global Assembly Cache.  Le Global Assembly Cache stocke les assemblys spécialement destinés à être partagés entre plusieurs applications sur l'ordinateur.  
  
 Vous ne devez partager des assemblys en les installant dans le Global Assembly Cache qu'en cas de nécessité.  En règle générale, vous devez garder les dépendances d'assembly privées et rechercher les assemblys dans le répertoire de l'application, à moins que le partage d'un assembly soit explicitement requis.  En outre, il n'est pas nécessaire d'installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.  
  
> [!NOTE]
>  Il existe des scénarios au cours desquels vous ne souhaitez explicitement pas installer un assembly dans le Global Assembly Cache.  Si vous placez l'un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ou installer l'application en utilisant la commande **xcopy** pour copier le répertoire de l'application.  Vous devez également déplacer l'assembly dans le Global Assembly Cache.  
  
 Il existe deux modes de déploiement d'un assembly dans le Global Assembly Cache :  
  
-   Utilisez un programme d'installation conçu pour fonctionner avec le Global Assembly Cache.  Il s'agit de l'option par défaut d'installation d'assemblys dans le Global Assembly Cache.  
  
-   Utilisez un outil de développement appelé [Outil Global Assembly Cache Tool \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) fourni avec le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Au cours de scénarios de déploiement, utilisez Windows Installer pour installer des assemblys dans le Global Assembly Cache.  Utilisez l'Explorateur Windows ou l'outil Global Assembly Cache Tool uniquement au cours de scénarios de développement, car il ne propose pas de fonctionnalités de décompte de références d'assembly ou d'autres fonctionnalités disponibles lors de l'utilisation de Windows Installer.  
  
 Depuis le .NET Framework 4, l'emplacement par défaut pour le Global Assembly Cache est **%windir%\\Microsoft.NET\\assembly**.  Dans les versions antérieures du .NET Framework, l'emplacement par défaut est **%windir%\\assembly**.  
  
 Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d'accès \(ACL, Access Control List\) pour contrôler l'accès en écriture et en exécution.  Le Global Assembly Cache étant installé dans un sous\-répertoire du répertoire systemroot, il hérite de la liste de contrôle d'accès \(ACL\) de ce répertoire.  Il est recommandé que seuls les utilisateurs disposant de privilèges d'administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.  
  
 Les assemblys déployés dans le Global Assembly Cache doivent avoir un nom fort.  Lorsqu'un assembly est ajouté au Global Assembly Cache, des contrôles d'intégrité sont effectués sur tous les fichiers qui composent l'assembly.  Le cache effectue ces contrôles d'intégrité pour vérifier qu'aucun assembly n'a été falsifié, par exemple, lorsqu'un fichier a été modifié, mais que le manifeste ne reflète pas cette modification.  
  
## Voir aussi  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [Utilisation d'assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)