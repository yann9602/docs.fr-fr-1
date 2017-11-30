---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="5cee6-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="5cee6-102">/optioncompare</span></span>
<span data-ttu-id="5cee6-103">Spécifie la façon dont sont effectuées les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5cee6-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cee6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cee6-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="5cee6-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="5cee6-105">Remarks</span></span>  
 <span data-ttu-id="5cee6-106">Vous pouvez spécifier `/optioncompare` dans un des deux formes : `/optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `/optioncompare:text` pour utiliser des comparaisons de chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="5cee6-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="5cee6-107">Par défaut, le compilateur utilise `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="5cee6-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="5cee6-108">Dans Microsoft Windows, la page de codes utilisée détermine l’ordre de tri binaire.</span><span class="sxs-lookup"><span data-stu-id="5cee6-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="5cee6-109">Un ordre de tri binaire standard est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5cee6-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="5cee6-110">Les comparaisons de chaînes de texte sont basées sur un ordre de tri de texte respectant la casse déterminé par les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="5cee6-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="5cee6-111">Un ordre de tri de texte par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5cee6-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="5cee6-112">Pour définir /optioncompare dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cee6-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="5cee6-113">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="5cee6-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5cee6-114">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5cee6-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5cee6-115">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5cee6-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="5cee6-116">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="5cee6-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="5cee6-117">Modifiez la valeur dans la **Option Compare** boîte.</span><span class="sxs-lookup"><span data-stu-id="5cee6-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="5cee6-118">Pour définir /optioncompare par programmation</span><span class="sxs-lookup"><span data-stu-id="5cee6-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="5cee6-119">Consultez [Option Compare, instruction](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5cee6-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cee6-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="5cee6-120">Example</span></span>  
 <span data-ttu-id="5cee6-121">Le code suivant compile `ProjFile.vb` et utilise des comparaisons de chaînes binaires.</span><span class="sxs-lookup"><span data-stu-id="5cee6-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cee6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cee6-122">See Also</span></span>  
 [<span data-ttu-id="5cee6-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cee6-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5cee6-124">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5cee6-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="5cee6-125">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="5cee6-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="5cee6-126">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="5cee6-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="5cee6-127">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="5cee6-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5cee6-128">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="5cee6-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="5cee6-129">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="5cee6-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
