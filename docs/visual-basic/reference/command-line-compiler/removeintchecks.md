---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="1a1a0-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="1a1a0-102">/removeintchecks</span></span>
<span data-ttu-id="1a1a0-103">Active la vérification des opérations sur les entiers ou désactivez les erreurs de dépassement.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a1a0-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a1a0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1a1a0-105">Arguments</span></span>  
  
|<span data-ttu-id="1a1a0-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1a1a0-106">Term</span></span>|<span data-ttu-id="1a1a0-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1a1a0-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1a1a0-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1a1a0-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1a1a0-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-109">Optional.</span></span> <span data-ttu-id="1a1a0-110">La `/removeintchecks-` option, le compilateur à vérifier tous les calculs d’entier pour les erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="1a1a0-111">La valeur par défaut est `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="1a1a0-112">Spécification de `/removeintchecks` ou `/removeintchecks+` empêche la vérification des erreurs et peuvent effectuer des calculs d’entier plus rapides.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="1a1a0-113">Toutefois, sans vérification des erreurs, et si les capacités de type données sont dépassées, des résultats incorrects peuvent être stockées sans déclencher d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="1a1a0-114">Pour définir /removeintchecks dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="1a1a0-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1a1a0-115">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1a1a0-116">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1a1a0-117">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1a1a0-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1a1a0-118">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1a1a0-119">3.  Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="1a1a0-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1a1a0-120">4.  Modifier la valeur de la **supprimer les contrôles de dépassement de capacité d’entier** boîte.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a1a0-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a1a0-121">Example</span></span>  
 <span data-ttu-id="1a1a0-122">Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement de capacité d’entier.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a1a0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a1a0-123">See Also</span></span>  
 [<span data-ttu-id="1a1a0-124">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a1a0-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1a1a0-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="1a1a0-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
