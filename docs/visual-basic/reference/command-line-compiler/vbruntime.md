---
title: /vbruntime | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 455f950988b540b74874ce38882c59059f77ea8f
ms.lasthandoff: 03/13/2017

---
# <a name="vbruntime"></a>/vbruntime
Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Compiler sans référence à la bibliothèque Runtime Visual Basic.  
  
 \+  
 Compiler avec une référence à la bibliothèque Visual Basic Runtime par défaut.  
  
 \*  
 Compiler sans référence à la bibliothèque Visual Basic Runtime et incorporer la fonctionnalité principale de la bibliothèque Runtime Visual Basic dans l’assembly.  
  
 `path`  
 Compiler avec une référence à la bibliothèque spécifiée (DLL).  
  
## <a name="remarks"></a>Remarques  
 La `/vbruntime` option du compilateur vous permet de spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic. Si vous compilez sans référence à la bibliothèque d’exécution Visual Basic, erreurs ou avertissements sont enregistrés sur les constructions de code ou de langage qui génèrent un appel à une application d’assistance du runtime Visual Basic. (A *du composant d’exécution Visual Basic* est une fonction définie dans Microsoft.VisualBasic.dll, qui est appelée lors de l’exécution pour exécuter une syntaxe de langue spécifique.)  
  
 Le `/vbruntime+` option produit le même comportement se produit si aucun `/vbruntime` le commutateur. Vous pouvez utiliser la `/vbruntime+` option permettant de remplacer la précédente `/vbruntime` commutateurs.  
  
 La plupart des objets de la `My` type ne sont pas disponibles lorsque vous utilisez la `/vbruntime-` ou `vbruntime:``path` options.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>L’incorporation de fonctionnalités principales Runtime de Visual Basic  
 La `/vbruntime*` option vous permet de compiler sans référence à une bibliothèque runtime. Au lieu de cela, les fonctionnalités principales de la bibliothèque Runtime Visual Basic sont incorporées dans l’assembly de l’utilisateur. Vous pouvez utiliser cette option si votre application s’exécute sur des plateformes qui ne contiennent pas le runtime Visual Basic.  
  
 Les membres du runtime suivants sont incorporés :  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions>(classe)</xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>(méthode)</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>(méthode)</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>(méthode)</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack>(constante)</xref:Microsoft.VisualBasic.Constants.vbBack>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr>(constante)</xref:Microsoft.VisualBasic.Constants.vbCr>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf>(constante)</xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed>(constante)</xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf>(constante)</xref:Microsoft.VisualBasic.Constants.vbLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine>(constante)</xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar>(constante)</xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString>(constante)</xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab>(constante)</xref:Microsoft.VisualBasic.Constants.vbTab>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>(constante)</xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
-   Certains objets de la `My` type  
  
 Si vous compilez à l’aide de la `/vbruntime*` option et votre code fait référence à un membre de la bibliothèque Runtime Visual Basic qui n’est pas incorporé avec la fonctionnalité principale, le compilateur renvoie une erreur indiquant que le membre n’est pas disponible.  
  
## <a name="referencing-a-specified-library"></a>Référencement d’une bibliothèque spécifiée  
 Vous pouvez utiliser la `path` argument pour compiler avec une référence à une bibliothèque runtime personnalisée au lieu de la bibliothèque Visual Basic Runtime par défaut.  
  
 Si la valeur de la `path` argument est un chemin d’accès complet à une DLL, le compilateur utilisera ce fichier comme bibliothèque runtime. Si la valeur de la `path` argument n’est pas un chemin d’accès complet à une DLL, le compilateur Visual Basic recherchera la DLL identifiée dans le dossier actif tout d’abord. Il recherche ensuite dans le chemin d’accès que vous avez spécifié à l’aide de la [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) option du compilateur. Si le `/sdkpath` option du compilateur n’est pas utilisée, le compilateur recherchera la DLL identifiée dans le dossier .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la `/vbruntime` option pour compiler avec une référence à une bibliothèque personnalisée.  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Base de Visual Basic – nouveau mode de compilation dans Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
