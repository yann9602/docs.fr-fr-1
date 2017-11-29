---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a><span data-ttu-id="570a3-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="570a3-102">/optioninfer</span></span>
<span data-ttu-id="570a3-103">Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.</span><span class="sxs-lookup"><span data-stu-id="570a3-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="570a3-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="570a3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="570a3-105">Arguments</span></span>  
  
|<span data-ttu-id="570a3-106">Terme</span><span class="sxs-lookup"><span data-stu-id="570a3-106">Term</span></span>|<span data-ttu-id="570a3-107">Définition</span><span class="sxs-lookup"><span data-stu-id="570a3-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="570a3-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="570a3-108">`+` &#124; `-`</span></span>|<span data-ttu-id="570a3-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="570a3-109">Optional.</span></span> <span data-ttu-id="570a3-110">Spécifiez `/optioninfer+` pour activer l'inférence de type de variable locale ou `/optioninfer-` pour la bloquer.</span><span class="sxs-lookup"><span data-stu-id="570a3-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="570a3-111">L'option `/optioninfer`, sans aucune valeur spécifiée, est identique à `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="570a3-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="570a3-112">La valeur par défaut en l'absence du commutateur `/optioninfer` est aussi `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="570a3-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="570a3-113">La valeur par défaut est définie dans le fichier réponse Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="570a3-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="570a3-114">Vous pouvez utiliser l'option `/noconfig` pour conserver les valeurs par défaut internes du compilateur au lieu de celles spécifiées dans le fichier vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="570a3-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="570a3-115">Pour cette option, la valeur par défaut du compilateur est `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="570a3-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="570a3-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="570a3-116">Remarks</span></span>  
 <span data-ttu-id="570a3-117">Si le fichier de code source contient un [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md), l’instruction substitue le `/optioninfer` paramètre du compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="570a3-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="570a3-118">Pour définir /optioninfer dans l'IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="570a3-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="570a3-119">Sélectionnez un projet dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="570a3-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="570a3-120">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="570a3-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="570a3-121">Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="570a3-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="570a3-122">Sur le **compiler** onglet, modifiez la valeur dans la **Option infer** boîte.</span><span class="sxs-lookup"><span data-stu-id="570a3-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="570a3-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="570a3-123">Example</span></span>  
 <span data-ttu-id="570a3-124">Le code suivant compile `test.vb` avec l'inférence de type de variable locale activée.</span><span class="sxs-lookup"><span data-stu-id="570a3-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="570a3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="570a3-125">See Also</span></span>  
 [<span data-ttu-id="570a3-126">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="570a3-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="570a3-127">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="570a3-127">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="570a3-128">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="570a3-128">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="570a3-129">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="570a3-129">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="570a3-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="570a3-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="570a3-131">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="570a3-131">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="570a3-132">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="570a3-132">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="570a3-133">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="570a3-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="570a3-134">Page Compiler, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="570a3-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="570a3-135">/noconfig</span><span class="sxs-lookup"><span data-stu-id="570a3-135">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="570a3-136">Génération à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="570a3-136">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
