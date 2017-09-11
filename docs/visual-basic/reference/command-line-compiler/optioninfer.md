---
title: /optioninfer | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioninfer
dev_langs:
- VB
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
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
ms.openlocfilehash: 4bcc35da2a255ca75805c8a918027d2ccb61b154
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="optioninfer"></a><span data-ttu-id="0cb08-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="0cb08-102">/optioninfer</span></span>
<span data-ttu-id="0cb08-103">Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.</span><span class="sxs-lookup"><span data-stu-id="0cb08-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cb08-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0cb08-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0cb08-105">Arguments</span></span>  
  
|<span data-ttu-id="0cb08-106">Terme</span><span class="sxs-lookup"><span data-stu-id="0cb08-106">Term</span></span>|<span data-ttu-id="0cb08-107">Définition</span><span class="sxs-lookup"><span data-stu-id="0cb08-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0cb08-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0cb08-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0cb08-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0cb08-109">Optional.</span></span> <span data-ttu-id="0cb08-110">Spécifiez `/optioninfer+` pour activer l'inférence de type de variable locale ou `/optioninfer-` pour la bloquer.</span><span class="sxs-lookup"><span data-stu-id="0cb08-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="0cb08-111">L'option `/optioninfer`, sans aucune valeur spécifiée, est identique à `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="0cb08-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="0cb08-112">La valeur par défaut en l'absence du commutateur `/optioninfer` est aussi `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="0cb08-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="0cb08-113">La valeur par défaut est définie dans le fichier réponse Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="0cb08-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0cb08-114">Vous pouvez utiliser l'option `/noconfig` pour conserver les valeurs par défaut internes du compilateur au lieu de celles spécifiées dans le fichier vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="0cb08-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="0cb08-115">Pour cette option, la valeur par défaut du compilateur est `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="0cb08-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb08-116">Notes</span><span class="sxs-lookup"><span data-stu-id="0cb08-116">Remarks</span></span>  
 <span data-ttu-id="0cb08-117">Si le fichier de code source contient une [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md), l’instruction substitue le `/optioninfer` du paramètre de compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0cb08-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="0cb08-118">Pour définir /optioninfer dans l'IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0cb08-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="0cb08-119">Sélectionnez un projet dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="0cb08-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="0cb08-120">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0cb08-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0cb08-121">Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="0cb08-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="0cb08-122">Sur le **compiler** onglet, modifiez la valeur dans la **Option infer** boîte.</span><span class="sxs-lookup"><span data-stu-id="0cb08-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cb08-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cb08-123">Example</span></span>  
 <span data-ttu-id="0cb08-124">Le code suivant compile `test.vb` avec l'inférence de type de variable locale activée.</span><span class="sxs-lookup"><span data-stu-id="0cb08-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cb08-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cb08-125">See Also</span></span>  
 <span data-ttu-id="0cb08-126">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0cb08-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="0cb08-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="0cb08-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="0cb08-130"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0cb08-131"> [Instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-131"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="0cb08-132"> [Inférence de Type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="0cb08-133"> [Boîte de dialogue Options par défaut, les projets, Visual Basic](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="0cb08-133"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="0cb08-134"> [Page Compiler, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="0cb08-134"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="0cb08-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="0cb08-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="0cb08-136"> [Génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="0cb08-136"> [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span></span>
