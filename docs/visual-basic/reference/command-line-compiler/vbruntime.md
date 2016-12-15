---
title: "/vbruntime | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbruntime"
  - "/vbruntime"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "vbruntime compiler option [Visual Basic]"
  - "-vbruntime compiler option [Visual Basic]"
  - "/vbruntime compiler option [Visual Basic]"
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /vbruntime
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que le compilateur doit compiler sans référence à la bibliothèque Visual Basic Runtime, ou avec une référence à une bibliothèque Runtime spécifique.  
  
## Syntaxe  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## Arguments  
 \-  
 Compiler sans référence à la bibliothèque Visual Basic Runtime.  
  
 \+  
 Compiler avec une référence à la bibliothèque Visual Basic Runtime par défaut.  
  
 \*  
 Compiler sans référence à la bibliothèque Visual Basic Runtime et incorporer la fonctionnalité principale de la bibliothèque Visual Basic Runtime dans l'assembly.  
  
 `path`  
 Compiler avec une référence à la bibliothèque spécifiée \(DLL\).  
  
## Notes  
 L'option du compilateur `/vbruntime` vous permet de spécifier que le compilateur doit compiler sans référence à la bibliothèque Visual Basic Runtime.  Si vous compilez sans référence à la bibliothèque Visual Basic Runtime, des erreurs ou avertissements sont consignés dans les constructions de code ou de langage qui génèrent un appel à une application d'assistance Visual Basic Runtime.  \(Une *application d'assistance Visual Basic Runtime* est une fonction définie dans Microsoft.VisualBasic.dll, qui est appelée pendant l'exécution pour exécuter une syntaxe de langue spécifique.\)  
  
 L'option `/vbruntime+` affiche le même comportement qui se produit si aucun commutateur `/vbruntime` n'est spécifié.  Vous pouvez utiliser l'option `/vbruntime+` pour substituer des commutateurs `/vbruntime` précédents.  
  
 La plupart des objets du type d' `My` sont pas disponibles lorsque vous utilisez `/vbruntime-` ou les options d' `vbruntime:``path` .  
  
## Incorporation de fonctionnalités principales Runtime Visual Basic  
 L'option `/vbruntime*` permet de compiler sans référence à une bibliothèque Runtime.  Au lieu de cela, la fonctionnalité principale de la bibliothèque Visual Basic Runtime est incorporée à l'assembly utilisateur.  Vous pouvez utiliser cette option si votre application s'exécute sur les plateformes qui ne contiennent pas Runtime Visual Basic.  
  
 Les membres du runtime suivants sont imbriqués :  
  
-   Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>.  
  
-   Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   Méthode <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbBack>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbCr>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbLf>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbTab>  
  
-   Constante <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
-   Certains objets du type d' `My`  
  
 Si vous compilez à l'aide de l'option `/vbruntime*` et que votre code fait référence à un membre de la bibliothèque Visual Basic Runtime qui n'est pas incorporé avec la fonctionnalité principale, le compilateur renvoie une erreur indiquant que le membre n'est pas disponible.  
  
## Références à une bibliothèque spécifiée  
 Vous pouvez utiliser l'argument `path` pour compiler avec une référence à une bibliothèque Runtime personnalisée à la place de la bibliothèque Visual Basic Runtime par défaut.  
  
 Si la valeur pour l'argument `path` est un chemin qualifié complet à une DLL, le compilateur utilisera ce fichier comme bibliothèque Runtime.  Si la valeur pour l'argument `path` n'est pas un chemin qualifié complet à une DLL, le compilateur Visual Basic recherchera d'abord la DLL identifiée dans le dossier actif.  Il recherchera ensuite dans le chemin d'accès que vous avez spécifié en utilisant l'option du compilateur [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).  Si l'option du compilateur `/sdkpath` n'est pas utilisée, le compilateur recherchera la DLL identifiée dans le dossier .NET Framework \(`%systemroot%\Microsoft.NET\Framework\versionNumber`\).  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'option `/vbruntime` pour compiler avec une référence à une bibliothèque personnalisée.  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## Voir aussi  
 [Le cœur de Visual Basic \- nouveau mode de compilation dans Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)