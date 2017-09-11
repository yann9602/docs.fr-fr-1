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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 375ec79fe2bf63bc03988ecaad877eb27f43d55b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="netcf"></a><span data-ttu-id="72bd9-102">/netcf</span><span class="sxs-lookup"><span data-stu-id="72bd9-102">/netcf</span></span>
<span data-ttu-id="72bd9-103">Configure le compilateur pour cibler le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span><span class="sxs-lookup"><span data-stu-id="72bd9-103">Sets the compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72bd9-104">Syntax</span></span>  
  
```  
/netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="72bd9-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="72bd9-105">Remarks</span></span>  
 <span data-ttu-id="72bd9-106">Le `/netcf` option entraîne le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur cible les [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] plutôt que la version complète [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="72bd9-106">The `/netcf` option causes the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] rather than the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="72bd9-107">Fonctionnalités de langage qui sont uniquement présentes dans la version complète [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] est désactivé.</span><span class="sxs-lookup"><span data-stu-id="72bd9-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="72bd9-108">Le `/netcf` option est conçue pour être utilisée avec [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="72bd9-108">The `/netcf` option is designed to be used with [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="72bd9-109">Les fonctionnalités de langue désactivées par `/netcf` sont les mêmes que celles absentes des fichiers ciblés avec `/sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="72bd9-109">The language features disabled by `/netcf` are the same language features not present in the files targeted with `/sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72bd9-110">La `/netcf` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="72bd9-110">The `/netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="72bd9-111">Le `/netcf` option est définie lorsque un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet smart device est chargé.</span><span class="sxs-lookup"><span data-stu-id="72bd9-111">The `/netcf` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="72bd9-112">La `/netcf` option modifie les fonctionnalités de langage suivantes :</span><span class="sxs-lookup"><span data-stu-id="72bd9-112">The `/netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="72bd9-113">Le [fin \<mot-clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) (mot clé), ce qui interrompt l’exécution d’un programme, est désactivé.</span><span class="sxs-lookup"><span data-stu-id="72bd9-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="72bd9-114">Le programme suivant compile et exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="72bd9-114">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="72bd9-115">[!code-vb[VbVbalrCompiler&#34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="72bd9-115">[!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span></span>  
  
-   <span data-ttu-id="72bd9-116">Liaison tardive, dans tous les formulaires est désactivée.</span><span class="sxs-lookup"><span data-stu-id="72bd9-116">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="72bd9-117">Erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrées.</span><span class="sxs-lookup"><span data-stu-id="72bd9-117">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="72bd9-118">Le programme suivant compile et exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="72bd9-118">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="72bd9-119">[!code-vb[VbVbalrCompiler&#35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="72bd9-119">[!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span></span>  
  
-   <span data-ttu-id="72bd9-120">Le [automatique](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificateurs sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="72bd9-120">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="72bd9-121">La syntaxe de la [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instruction est également modifiée pour `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="72bd9-121">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="72bd9-122">Le code suivant montre l’effet de `/netcf` sur une compilation.</span><span class="sxs-lookup"><span data-stu-id="72bd9-122">The following code shows the effect of `/netcf` on a compilation.</span></span>  
  
     <span data-ttu-id="72bd9-123">[!code-vb[VbVbalrCompiler n °&36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="72bd9-123">[!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span></span>  
  
-   <span data-ttu-id="72bd9-124">À l’aide de mots clés Visual Basic 6.0 qui ont été supprimés de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur différente lorsque `/netcf` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="72bd9-124">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a different error when `/netcf` is used.</span></span> <span data-ttu-id="72bd9-125">Cela affecte les messages d’erreur pour les mots clés suivants :</span><span class="sxs-lookup"><span data-stu-id="72bd9-125">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="72bd9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="72bd9-126">Example</span></span>  
 <span data-ttu-id="72bd9-127">Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="72bd9-127">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="72bd9-128">En général, vous utilisez la version la plus récente de la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span><span class="sxs-lookup"><span data-stu-id="72bd9-128">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="72bd9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72bd9-129">See Also</span></span>  
 <span data-ttu-id="72bd9-130">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="72bd9-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="72bd9-131"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="72bd9-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="72bd9-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="72bd9-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
