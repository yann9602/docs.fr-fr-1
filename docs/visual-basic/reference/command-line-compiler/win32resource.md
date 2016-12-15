---
title: "/win32resource | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/win32resource"
  - "win32resource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/win32resource compiler option [Visual Basic]"
  - "-win32resource compiler option [Visual Basic]"
  - "win32resource compiler option [Visual Basic]"
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32resource
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Insère un fichier de ressources Win32 dans le fichier de sortie.  
  
## Syntaxe  
  
```  
/win32resource:filename  
```  
  
## Arguments  
 `filename`  
 Nom du fichier de ressources à ajouter à votre fichier de sortie.  Mettez le nom de fichier entre guillemets \(" "\) s'il contient un espace.  
  
## Notes  
 Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressources \(RC\) Microsoft Windows.  
  
 Une ressource Win32 peut contenir les informations de version ou de bitmap \(icône\) qui permet d'identifier votre application dans **Explorateur de fichiers**.  Si vous ne spécifiez pas `/win32resource`, le compilateur génère des informations sur la version en fonction de la version de l'assembly.  Les options `/win32resource` et `/win32icon` s'excluent mutuellement.  
  
 Consultez [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un fichier de ressource [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] ou [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md) pour joindre un fichier de ressource [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  L'option `/win32resource` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `In.vb` et le lie au fichier de ressources Win32 `Rf.res` :  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)