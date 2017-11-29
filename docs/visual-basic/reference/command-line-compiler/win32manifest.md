---
title: /win32manifest (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a46641181c3ff66882468f8372bb97c3a49a8462
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="win32manifest-visual-basic"></a>/win32manifest (Visual Basic)
Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileName`|Le chemin d’accès du fichier manifest personnalisé.|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, le compilateur Visual Basic incorpore un manifeste d’application qui spécifie le niveau d’exécution demandé asInvoker. Il crée le manifeste dans le même dossier que celui dans lequel le fichier exécutable est généré, en général le dossier bin\Debug ou bin\Release lorsque vous utilisez Visual Studio. Si vous souhaitez fournir un manifeste personnalisé, par exemple, pour spécifier un niveau d’exécution demandé de highestAvailable ou requireAdministrator, utilisez cette option pour spécifier le nom du fichier.  
  
> [!NOTE]
>  Cette option et la [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option s’excluent mutuellement. Si vous essayez d’utiliser les deux options dans la même ligne de commande, vous obtiendrez une erreur de build.  
  
 Une application sans manifeste d’application pour spécifier le niveau d’exécution requis est soumise à une virtualisation des fichiers/registres sous la fonctionnalité de contrôle de compte d’utilisateur de Windows Vista. Pour plus d’informations sur la virtualisation, consultez [déploiement ClickOnce sur Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Votre application sera soumis à la virtualisation si une des conditions suivantes est vraie :  
  
1.  Vous utilisez la `/nowin32manifest` option et si vous ne fournissez pas de manifeste dans une étape de génération ultérieure ou en tant que partie d’un fichier de ressources Windows (.res) à l’aide de la `/win32resource` option.  
  
2.  Vous fournissez un manifeste personnalisé qui ne spécifie pas le niveau d’exécution requis.  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] crée un fichier .manifest par défaut et le stocke dans les répertoires debug et release avec le fichier exécutable. Vous pouvez afficher ou modifier le fichier App.manifest par défaut en cliquant sur **afficher les paramètres UAC** sur la **Application** onglet dans le Concepteur de projet. Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Vous pouvez fournir le manifeste d’application comme une étape post-build personnalisée ou en tant que partie d’un fichier de ressources Win32 à l’aide de la `/nowin32manifest` option. Utilisez cette même option pour que votre application soit soumise à la virtualisation des fichiers ou des registres dans Windows Vista. Cela empêchera le compilateur de créer et d’incorporer un manifeste par défaut dans le fichier PE.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le manifeste par défaut que le compilateur Visual Basic insère dans un PE.  
  
> [!NOTE]
>  Le compilateur insère un nom d’application standard, MyApplication.app, dans le manifeste XML. Cela permet aux applications de s’exécuter dans Windows Server 2003 Service Pack 3.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
