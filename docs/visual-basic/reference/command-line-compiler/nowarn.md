---
title: /nowarn | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
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
ms.openlocfilehash: 308bf24c2a397a75f36b97062dde7380b90c8994
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="nowarn"></a><span data-ttu-id="c4489-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="c4489-102">/nowarn</span></span>
<span data-ttu-id="c4489-103">Supprime la capacité du compilateur à générer des avertissements.</span><span class="sxs-lookup"><span data-stu-id="c4489-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4489-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4489-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4489-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c4489-105">Arguments</span></span>  
  
|<span data-ttu-id="c4489-106">Terme</span><span class="sxs-lookup"><span data-stu-id="c4489-106">Term</span></span>|<span data-ttu-id="c4489-107">Définition</span><span class="sxs-lookup"><span data-stu-id="c4489-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="c4489-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4489-108">Optional.</span></span> <span data-ttu-id="c4489-109">Liste délimitée par des virgules des numéros d’identification avertissement que le compilateur doit supprimer.</span><span class="sxs-lookup"><span data-stu-id="c4489-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="c4489-110">Si l’ID d’avertissement ne sont spécifié, tous les avertissements sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="c4489-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4489-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c4489-111">Remarks</span></span>  
 <span data-ttu-id="c4489-112">La `/nowarn` option, le compilateur ne génère ne pas les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c4489-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="c4489-113">Pour supprimer un avertissement, fournissez l’ID d’avertissement pour la `/nowarn` option suit le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="c4489-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="c4489-114">Séparez plusieurs numéros d’avertissement par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c4489-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="c4489-115">Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4489-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="c4489-116">Par exemple, si vous souhaitez supprimer BC42024, numéro d’avertissement pour les variables locales inutilisées, spécifiez `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="c4489-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="c4489-117">Pour plus d’informations sur les numéros d’avertissement, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c4489-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="c4489-118">Pour définir /nowarn dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="c4489-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c4489-119">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="c4489-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c4489-120">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c4489-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="c4489-121">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="c4489-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="c4489-122">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="c4489-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c4489-123">3.  Sélectionnez le **désactiver tous les avertissements** case à cocher pour désactiver tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c4489-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="c4489-124">ou</span><span class="sxs-lookup"><span data-stu-id="c4489-124">- or -</span></span><br />     <span data-ttu-id="c4489-125">Pour désactiver un avertissement particulier, cliquez sur **aucun** dans la liste déroulante adjacente à l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4489-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4489-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4489-126">Example</span></span>  
 <span data-ttu-id="c4489-127">Le code suivant compile `T2.vb` et n’affiche pas d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="c4489-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="c4489-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4489-128">Example</span></span>  
 <span data-ttu-id="c4489-129">Le code suivant compile `T2.vb` et n’affiche pas les avertissements pour les variables locales inutilisées (42024).</span><span class="sxs-lookup"><span data-stu-id="c4489-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4489-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4489-130">See Also</span></span>  
 <span data-ttu-id="c4489-131">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="c4489-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="c4489-132"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="c4489-132"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="c4489-133"> [Configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="c4489-133"> [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span></span>
