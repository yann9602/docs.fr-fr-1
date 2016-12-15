---
title: "/out (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "/out compiler option [Visual Basic]"
  - "-out compiler option [Visual Basic]"
  - "out compiler option [Visual Basic]"
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /out (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie le nom du fichier de sortie.  
  
## Syntaxe  
  
```  
/out:filename  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`filename`|Obligatoire.  Nom du fichier de sortie créé par le compilateur.  Si le nom de fichier contient un espace, mettez le nom entre guillemets \(" "\).|  
  
## Notes  
 Spécifiez le nom complet et l'extension du fichier à créer.  Dans le cas contraire, le fichier .exe tire son nom du fichier de code source contenant la procédure `Sub Main`, et le fichier .dll tire son nom du premier fichier de code source.  
  
 Si vous spécifiez un nom de fichier sans une extension .exe ou .dll, le compilateur ajoute automatiquement l'extension pour vous, selon la valeur spécifiée pour l'option du compilateur `/target`.  
  
||  
|-|  
|Pour définir \/out dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Application**.<br />3.  Modifiez la valeur dans la zone **Nom de l'assembly**.|  
  
## Exemple  
 Le code suivant compile `T2.vb` et crée un fichier de sortie `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)