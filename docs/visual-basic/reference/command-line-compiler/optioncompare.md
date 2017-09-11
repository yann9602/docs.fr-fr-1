---
title: /optioncompare | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c9512427cda0b6a3bcb0c1fe338b47ff9f779d19
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="optioncompare"></a><span data-ttu-id="ba03a-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="ba03a-102">/optioncompare</span></span>
<span data-ttu-id="ba03a-103">Spécifie la façon dont sont effectuées les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="ba03a-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba03a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba03a-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba03a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ba03a-105">Remarks</span></span>  
 <span data-ttu-id="ba03a-106">Vous pouvez spécifier `/optioncompare` dans une des deux formes : `/optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `/optioncompare:text` pour utiliser des comparaisons de chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="ba03a-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="ba03a-107">Par défaut, le compilateur utilise `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="ba03a-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="ba03a-108">Dans Microsoft Windows, la page de codes utilisée détermine l’ordre de tri binaire.</span><span class="sxs-lookup"><span data-stu-id="ba03a-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="ba03a-109">Un ordre de tri binaire standard est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ba03a-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="ba03a-110">Les comparaisons de chaînes de texte sont basées sur un ordre de tri de texte respectant la casse déterminé par les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="ba03a-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="ba03a-111">Un ordre de tri de texte par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ba03a-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="ba03a-112">Pour définir /optioncompare dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba03a-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="ba03a-113">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="ba03a-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ba03a-114">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ba03a-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="ba03a-115">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="ba03a-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="ba03a-116">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="ba03a-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ba03a-117">Modifiez la valeur dans la **Option Compare** boîte.</span><span class="sxs-lookup"><span data-stu-id="ba03a-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="ba03a-118">Pour définir /optioncompare par programme</span><span class="sxs-lookup"><span data-stu-id="ba03a-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="ba03a-119">Consultez la page [Option Compare, instruction](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ba03a-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba03a-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba03a-120">Example</span></span>  
 <span data-ttu-id="ba03a-121">Le code suivant compile P`rojFile.vb` et utilise des comparaisons de chaînes binaires.</span><span class="sxs-lookup"><span data-stu-id="ba03a-121">The following code compiles P`rojFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba03a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba03a-122">See Also</span></span>  
 <span data-ttu-id="ba03a-123">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="ba03a-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="ba03a-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="ba03a-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="ba03a-127"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="ba03a-128"> [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ba03a-128"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="ba03a-129"> [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="ba03a-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
