---
title: /netcf | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
dev_langs:
- VB
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
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
ms.openlocfilehash: d8e2328eb5434ea0e73238709c429975ae29e6d0
ms.lasthandoff: 03/13/2017

---
# <a name="netcf"></a>/netcf
Configure le compilateur pour cibler le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>Remarques  
 Le `/netcf` option entraîne le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur cible les [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] plutôt que la version complète [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Fonctionnalités de langage qui sont uniquement présentes dans la version complète [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] est désactivé.  
  
 Le `/netcf` option est conçue pour être utilisée avec [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Les fonctionnalités de langue désactivées par `/netcf` sont les mêmes que celles absentes des fichiers ciblés avec `/sdkpath`.  
  
> [!NOTE]
>  La `/netcf` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande. Le `/netcf` option est définie lorsque un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet smart device est chargé.  
  
 La `/netcf` option modifie les fonctionnalités de langage suivantes :  
  
-   Le [fin \<mot-clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) (mot clé), ce qui interrompt l’exécution d’un programme, est désactivé. Le programme suivant compile et exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.  
  
     [!code-vb[VbVbalrCompiler&#34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Liaison tardive, dans tous les formulaires est désactivée. Erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrées. Le programme suivant compile et exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.  
  
     [!code-vb[VbVbalrCompiler&#35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   Le [automatique](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificateurs sont désactivées. La syntaxe de la [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instruction est également modifiée pour `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Le code suivant montre l’effet de `/netcf` sur une compilation.  
  
     [!code-vb[VbVbalrCompiler n °&36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   À l’aide de mots clés Visual Basic 6.0 qui ont été supprimés de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur différente lorsque `/netcf` est utilisé. Cela affecte les messages d’erreur pour les mots clés suivants :  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] sur le lecteur C. En général, vous utilisez la version la plus récente de la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
