---
title: /win32manifest (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b07d5816e5bb80a95e608fa7214a2db48ebac0dc
ms.lasthandoff: 03/13/2017

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
|`fileName`|Le chemin d’accès du fichier manifeste personnalisé.|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, le compilateur Visual Basic incorpore un manifeste d’application qui spécifie le niveau d’exécution demandé asInvoker. Il crée le manifeste dans le même dossier que celui dans lequel le fichier exécutable est généré, en général le dossier bin\Debug ou bin\Release lorsque vous utilisez Visual Studio. Si vous souhaitez fournir un manifeste personnalisé, par exemple, pour spécifier le niveau d’exécution demandé de « highestAvailable » ou requireAdministrator, utilisez cette option pour spécifier le nom du fichier.  
  
> [!NOTE]
>  Cette option et la [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option s’excluent mutuellement. Si vous essayez d’utiliser les deux options dans la même ligne de commande, vous obtiendrez une erreur de build.  
  
 Une application qui n’a aucune application manifeste qui spécifie qu'un niveau d’exécution demandé sera soumis à la virtualisation de fichiers et du Registre sous la fonctionnalité contrôle de compte d’utilisateur dans Windows Vista. Pour plus d’informations sur la virtualisation, consultez [déploiement ClickOnce sur Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Votre application sera soumis à la virtualisation si une des conditions suivantes est vraie :  
  
1.  Vous utilisez la `/nowin32manifest` option et si vous ne fournissez pas de manifeste dans une étape de génération ultérieure ou en tant que partie d’un fichier de ressources Windows (.res) à l’aide de la `/win32resource` option.  
  
2.  Vous fournissez un manifeste personnalisé qui ne spécifie pas un niveau d’exécution demandé.  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]Crée un fichier .manifest de valeur par défaut et le stocke dans les répertoires debug et release avec le fichier exécutable. Vous pouvez afficher ou modifier le fichier App.manifest par défaut en cliquant sur **afficher les paramètres UAC** sur la **Application** onglet du Concepteur de projet. Pour plus d’informations, consultez [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Vous pouvez fournir le manifeste d’application comme une étape après génération personnalisée ou en tant que partie d’un fichier de ressources Win32 à l’aide de la `/nowin32manifest` option. Utilisez cette même option si vous souhaitez que votre application soit soumis à la virtualisation de fichiers ou du Registre dans Windows Vista. Cela empêchera le compilateur de créer et d’incorporer un manifeste par défaut dans le fichier PE.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente le manifeste par défaut que le compilateur Visual Basic insère dans un PE.  
  
> [!NOTE]
>  Le compilateur insère un nom d’application standard, MyApplication.app, au manifeste XML. Il s’agit d’une solution de contournement pour permettre aux applications de s’exécuter sur Windows Server 2003 Service Pack 3.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
