---
title: /warnaserror (Visual Basic) | Documents Microsoft
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
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
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
ms.openlocfilehash: 8ed72415a75860b34e37c2bf4fc686cdae37f69e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="b5754-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5754-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="b5754-103">Entraîne le compilateur à traiter la première occurrence d’un avertissement comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="b5754-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5754-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5754-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5754-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5754-105">Arguments</span></span>  
  
|<span data-ttu-id="b5754-106">Terme</span><span class="sxs-lookup"><span data-stu-id="b5754-106">Term</span></span>|<span data-ttu-id="b5754-107">Définition</span><span class="sxs-lookup"><span data-stu-id="b5754-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="b5754-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="b5754-108">+ &#124; -</span></span>|<span data-ttu-id="b5754-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5754-109">Optional.</span></span> <span data-ttu-id="b5754-110">Par défaut, `/warnaserror-` est en vigueur, les avertissements n’empêchent pas le compilateur de générer un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="b5754-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="b5754-111">Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b5754-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="b5754-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5754-112">Optional.</span></span> <span data-ttu-id="b5754-113">Liste délimitée par des virgules l’ID d’avertissement numéros auquel la `/warnaserror` option s’applique.</span><span class="sxs-lookup"><span data-stu-id="b5754-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="b5754-114">Si aucun ID d’avertissement n’est spécifié, la `/warnaserror` option s’applique à tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="b5754-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5754-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="b5754-115">Remarks</span></span>  
 <span data-ttu-id="b5754-116">La `/warnaserror` option considère tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b5754-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="b5754-117">Tous les messages qui normalement devraient être affichés comme avertissements apparaissent comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b5754-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="b5754-118">Le compilateur signale les occurrences ultérieures du même avertissement en tant qu’avertissements.</span><span class="sxs-lookup"><span data-stu-id="b5754-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="b5754-119">Par défaut, `/warnaserror-` est en vigueur, ce qui provoque les avertissements d’information uniquement.</span><span class="sxs-lookup"><span data-stu-id="b5754-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="b5754-120">Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b5754-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="b5754-121">Si vous souhaitez que seuls certains avertissements spécifiques à traiter comme des erreurs, vous pouvez spécifier une liste séparée par des virgules des numéros d’avertissement à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b5754-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5754-122">La `/warnaserror` option ne contrôle pas l’affichage des avertissements.</span><span class="sxs-lookup"><span data-stu-id="b5754-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="b5754-123">Utilisez le [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option pour désactiver les avertissements.</span><span class="sxs-lookup"><span data-stu-id="b5754-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="b5754-124">Pour définir /warnaserror pour traiter tous les avertissements comme des erreurs dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b5754-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="b5754-125">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="b5754-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b5754-126">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b5754-126">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="b5754-127">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="b5754-127">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="b5754-128">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="b5754-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b5754-129">3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b5754-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="b5754-130">4.  Vérifier la **traiter tous les avertissements comme des erreurs** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="b5754-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="b5754-131">Pour définir /warnaserror pour traiter les avertissements spécifiques comme des erreurs dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b5754-131">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="b5754-132">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="b5754-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b5754-133">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b5754-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="b5754-134">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="b5754-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b5754-135">3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b5754-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="b5754-136">4.  Assurez-vous que le **traiter tous les avertissements comme des erreurs** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b5754-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="b5754-137">5.  Sélectionnez **erreur** à partir de la **Notification** colonne adjacente à l’avertissement qui doit être traitée comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="b5754-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b5754-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5754-138">Example</span></span>  
 <span data-ttu-id="b5754-139">Le code suivant compile `In.vb` et demande au compilateur d’afficher une erreur pour la première occurrence de chaque avertissement rencontré.</span><span class="sxs-lookup"><span data-stu-id="b5754-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="b5754-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5754-140">Example</span></span>  
 <span data-ttu-id="b5754-141">Le code suivant compile `T2.vb` et traite uniquement l’avertissement pour les variables locales inutilisées (42024) comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="b5754-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5754-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5754-142">See Also</span></span>  
 <span data-ttu-id="b5754-143">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5754-143">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b5754-144"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="b5754-144"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="b5754-145"> [Configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="b5754-145"> [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span></span>
