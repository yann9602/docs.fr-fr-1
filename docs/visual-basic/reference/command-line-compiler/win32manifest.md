---
title: "/win32manifest (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/win32manifest compiler option [Visual Basic]"
  - "win32manifest compiler option [Visual Basic]"
  - "-win32manifest compiler option [Visual Basic]"
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Identifie un fichier de manifeste de l'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable \(PE\) d'un projet.  
  
## Syntaxe  
  
```  
/win32manifest: fileName  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`fileName`|Chemin d'accès relatif au fichier manifeste personnalisé.|  
  
## Notes  
 Par défaut, le compilateur Visual Basic incorpore un manifeste de l'application, qui spécifie le niveau d'exécution requis « asInvoker ».  Il crée le manifeste dans le même dossier que celui dans lequel le fichier exécutable a été généré, normalement le dossier bin\\Debug ou bin\\Release, lorsque vous utilisez Visual Studio.  Pour fournir un manifeste personnalisé, par exemple pour spécifier le niveau d'exécution requis « highestAvailable » ou « requireAdministrator », utilisez cette option pour indiquer le nom du fichier.  
  
> [!NOTE]
>  Cette option et l'option [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) sont mutuellement exclusives.  Si vous tentez d'utiliser ces deux options dans la même ligne de commande, une erreur de build se produit.  
  
 Une application sans manifeste d'application pour spécifier le niveau d'exécution requis est soumise à une virtualisation des fichiers\/registres sous la fonction de contrôle de compte utilisateur de Windows Vista.  Pour plus d'informations sur la virtualisation, consultez [ClickOnce Deployment on Windows Vista](/visual-studio/deployment/clickonce-deployment-on-windows-vista).  
  
 Votre application est soumise à virtualisation, si l'une des conditions suivantes est vraie :  
  
1.  Vous utilisez l'option `/nowin32manifest` sans fournir de manifeste au cours d'une étape de génération ultérieure ou en tant que partie du fichier de ressources Windows \(.res\) à l'aide de l'option `/win32resource`.  
  
2.  Vous fournissez un manifeste personnalisé qui ne spécifie pas le niveau d'exécution requis.  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] crée un fichier .manifest par défaut et le stocke dans les répertoires debug et release avec le fichier exécutable.  Vous pouvez afficher ou modifier le fichier app.manifest par défaut, en cliquant sur **Afficher les paramètres UAC** dans l'onglet **Application** du Concepteur de projets. Pour plus d'informations, consultez [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
 Vous pouvez fournir le manifeste d'application en tant qu'étape après génération personnalisée ou en tant que partie d'un fichier de ressources Win32 à l'aide de l'option `/nowin32manifest`.  Utilisez cette même option pour que votre application soit soumise à la virtualisation des fichiers ou des registres dans Windows Vista.  Cela empêche le compilateur de créer et d'incorporer un manifeste par défaut dans le fichier PE.  
  
## Exemple  
 L'exemple suivant présente le manifeste par défaut que le compilateur Visual Basic insère dans un PE.  
  
> [!NOTE]
>  Le compilateur insère un nom d'application standard, MyApplication.app, au manifeste XML.  Cela permet aux applications de s'exécuter sous Windows Server 2003 Service Pack 3.  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)