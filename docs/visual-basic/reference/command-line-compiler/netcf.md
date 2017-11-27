---
title: /netcf
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a75573b0881af71e907a488c2b3c15db3816fc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="netcf"></a><span data-ttu-id="4e515-102">/netcf</span><span class="sxs-lookup"><span data-stu-id="4e515-102">/netcf</span></span>
<span data-ttu-id="4e515-103">Configure le compilateur pour cibler le [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e515-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e515-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e515-104">Syntax</span></span>  
  
```  
/netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e515-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e515-105">Remarks</span></span>  
 <span data-ttu-id="4e515-106">Le `/netcf` option entraîne la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur pour cibler le [!INCLUDE[Compact](~/includes/compact-md.md)] au lieu de la version complète [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e515-106">The `/netcf` option causes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4e515-107">Fonctionnalités de langage qui sont uniquement présentes dans la version complète [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] est désactivé.</span><span class="sxs-lookup"><span data-stu-id="4e515-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="4e515-108">Le `/netcf` option est conçue pour être utilisée avec [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="4e515-108">The `/netcf` option is designed to be used with [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="4e515-109">Les fonctionnalités de langue désactivées par `/netcf` sont les mêmes fonctionnalités de langage ne figure pas dans les fichiers ciblés avec `/sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="4e515-109">The language features disabled by `/netcf` are the same language features not present in the files targeted with `/sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e515-110">Le `/netcf` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4e515-110">The `/netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="4e515-111">Le `/netcf` option est définie lorsque un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projet smart device est chargé.</span><span class="sxs-lookup"><span data-stu-id="4e515-111">The `/netcf` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="4e515-112">Le `/netcf` option modifie les fonctionnalités de langage suivantes :</span><span class="sxs-lookup"><span data-stu-id="4e515-112">The `/netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="4e515-113">Le [fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) (mot clé), ce qui interrompt l’exécution d’un programme, est désactivé.</span><span class="sxs-lookup"><span data-stu-id="4e515-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="4e515-114">Le programme suivant compile et s’exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="4e515-114">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="4e515-115">Liaison tardive dans chacun des formulaires est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4e515-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="4e515-116">Erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrées.</span><span class="sxs-lookup"><span data-stu-id="4e515-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="4e515-117">Le programme suivant compile et s’exécute sans `/netcf` mais échoue au moment de la compilation avec `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="4e515-117">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="4e515-118">Le [automatique](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificateurs sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="4e515-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="4e515-119">La syntaxe de la [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) est également modifier l’instruction à `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="4e515-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="4e515-120">Le code suivant montre l’effet de `/netcf` sur une compilation.</span><span class="sxs-lookup"><span data-stu-id="4e515-120">The following code shows the effect of `/netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="4e515-121">À l’aide de mots clés Visual Basic 6.0 qui ont été supprimés de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] génère une erreur différente lorsque `/netcf` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4e515-121">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a different error when `/netcf` is used.</span></span> <span data-ttu-id="4e515-122">Cela affecte les messages d’erreur pour les mots clés suivants :</span><span class="sxs-lookup"><span data-stu-id="4e515-122">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4e515-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e515-123">Example</span></span>  
 <span data-ttu-id="4e515-124">Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](~/includes/compact-md.md)], l’utilisation des versions de mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de la [!INCLUDE[Compact](~/includes/compact-md.md)] sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="4e515-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="4e515-125">En règle générale, vous utiliseriez la version la plus récente de la [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e515-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e515-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e515-126">See Also</span></span>  
 [<span data-ttu-id="4e515-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e515-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4e515-128">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="4e515-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4e515-129">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="4e515-129">/sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
