---
title: /removeintchecks | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
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
ms.openlocfilehash: 25f67774238c6e9a6b3a2c50b3702e43d5a6374c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="removeintchecks"></a><span data-ttu-id="9b925-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="9b925-102">/removeintchecks</span></span>
<span data-ttu-id="9b925-103">Active la vérification des opérations d’entiers ou d’erreur de dépassement.</span><span class="sxs-lookup"><span data-stu-id="9b925-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b925-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b925-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b925-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b925-105">Arguments</span></span>  
  
|<span data-ttu-id="9b925-106">Terme</span><span class="sxs-lookup"><span data-stu-id="9b925-106">Term</span></span>|<span data-ttu-id="9b925-107">Définition</span><span class="sxs-lookup"><span data-stu-id="9b925-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="9b925-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9b925-108">`+` &#124; `-`</span></span>|<span data-ttu-id="9b925-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9b925-109">Optional.</span></span> <span data-ttu-id="9b925-110">La `/removeintchecks-` option, le compilateur à vérifier tous les calculs d’entier pour les erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="9b925-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="9b925-111">La valeur par défaut est `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="9b925-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="9b925-112">Spécification de `/removeintchecks` ou `/removeintchecks+` empêche la vérification des erreurs et peuvent effectuer des calculs d’entier plus rapides.</span><span class="sxs-lookup"><span data-stu-id="9b925-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="9b925-113">Toutefois, sans vérification des erreurs, et si les capacités de type données sont dépassées, des résultats incorrects peuvent être stockées sans le déclenchement d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="9b925-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="9b925-114">Pour définir /removeintchecks dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="9b925-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9b925-115">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="9b925-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9b925-116">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9b925-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9b925-117">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9b925-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="9b925-118">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="9b925-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9b925-119">3.  Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="9b925-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="9b925-120">4.  Modifiez la valeur de la **supprimer les contrôles de dépassement de capacité d’entier** boîte.</span><span class="sxs-lookup"><span data-stu-id="9b925-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9b925-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b925-121">Example</span></span>  
 <span data-ttu-id="9b925-122">Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement d’entier.</span><span class="sxs-lookup"><span data-stu-id="9b925-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b925-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b925-123">See Also</span></span>  
 <span data-ttu-id="9b925-124">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b925-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="9b925-125"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="9b925-125"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
