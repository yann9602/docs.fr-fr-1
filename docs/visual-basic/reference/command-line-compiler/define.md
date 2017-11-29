---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="630cf-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="630cf-102">/define (Visual Basic)</span></span>
<span data-ttu-id="630cf-103">Définit des constantes conditionnelles du compilateur.</span><span class="sxs-lookup"><span data-stu-id="630cf-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="630cf-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="630cf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="630cf-105">Arguments</span></span>  
  
|<span data-ttu-id="630cf-106">Terme</span><span class="sxs-lookup"><span data-stu-id="630cf-106">Term</span></span>|<span data-ttu-id="630cf-107">Définition</span><span class="sxs-lookup"><span data-stu-id="630cf-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="630cf-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="630cf-108">Required.</span></span> <span data-ttu-id="630cf-109">Symbole à définir.</span><span class="sxs-lookup"><span data-stu-id="630cf-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="630cf-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="630cf-110">Optional.</span></span> <span data-ttu-id="630cf-111">Valeur à affecter au `symbol`.</span><span class="sxs-lookup"><span data-stu-id="630cf-111">The value to assign `symbol`.</span></span> <span data-ttu-id="630cf-112">Si `value` est une chaîne, elle doit être entourée par des séquences de barre oblique inverse/guillemets (\\») au lieu des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="630cf-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="630cf-113">Si aucune valeur n'est spécifiée, il prend la valeur True.</span><span class="sxs-lookup"><span data-stu-id="630cf-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="630cf-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="630cf-114">Remarks</span></span>  
 <span data-ttu-id="630cf-115">Le `/define` option a un effet semblable à l’aide un `#Const` directive de préprocesseur dans votre fichier source, excepté que les constantes définies avec `/define` sont publiques et s’appliquent à tous les fichiers dans le projet.</span><span class="sxs-lookup"><span data-stu-id="630cf-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="630cf-116">Vous pouvez utiliser les symboles créés par cette option avec la directive `#If`...`Then`...`#Else` pour effectuer une compilation conditionnelle des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="630cf-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="630cf-117">`/d` est la forme abrégée de `/define`.</span><span class="sxs-lookup"><span data-stu-id="630cf-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="630cf-118">Vous pouvez définir plusieurs symboles avec `/define` en utilisant une virgule pour séparer les définitions de symbole.</span><span class="sxs-lookup"><span data-stu-id="630cf-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="630cf-119">Pour définir /define dans l'environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="630cf-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="630cf-120">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="630cf-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="630cf-121">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="630cf-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="630cf-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="630cf-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="630cf-123">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="630cf-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="630cf-124">3.  Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="630cf-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="630cf-125">4.  Modifiez la valeur dans la **constantes personnalisées** boîte.</span><span class="sxs-lookup"><span data-stu-id="630cf-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="630cf-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="630cf-126">Example</span></span>  
 <span data-ttu-id="630cf-127">Le code suivant définit deux constantes de compilation conditionnelle, puis les utilise.</span><span class="sxs-lookup"><span data-stu-id="630cf-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="630cf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="630cf-128">See Also</span></span>  
 [<span data-ttu-id="630cf-129">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="630cf-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="630cf-130">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="630cf-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="630cf-131">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="630cf-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="630cf-132">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="630cf-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
