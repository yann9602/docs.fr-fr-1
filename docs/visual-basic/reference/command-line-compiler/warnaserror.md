---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04b79b3d14a9c4a9f9721860cd1ed44032dfa5d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="3e712-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e712-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="3e712-103">Indique au compilateur de traiter la première occurrence d’un avertissement comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="3e712-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e712-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e712-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e712-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e712-105">Arguments</span></span>  
  
|<span data-ttu-id="3e712-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3e712-106">Term</span></span>|<span data-ttu-id="3e712-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3e712-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3e712-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="3e712-108">+ &#124; -</span></span>|<span data-ttu-id="3e712-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e712-109">Optional.</span></span> <span data-ttu-id="3e712-110">Par défaut, `/warnaserror-` est en vigueur ; les avertissements n’empêchent pas le compilateur de générer un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="3e712-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="3e712-111">Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e712-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="3e712-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e712-112">Optional.</span></span> <span data-ttu-id="3e712-113">Liste délimitée par des virgules l’ID d’avertissement numéros à laquelle le `/warnaserror` option s’applique.</span><span class="sxs-lookup"><span data-stu-id="3e712-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="3e712-114">Si aucun ID d’avertissement n’est spécifié, le `/warnaserror` option s’applique à tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="3e712-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e712-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e712-115">Remarks</span></span>  
 <span data-ttu-id="3e712-116">Le `/warnaserror` option traite tous les avertissements comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e712-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="3e712-117">Les messages qui seraient normalement signalés comme avertissements apparaissent comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e712-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="3e712-118">Le compilateur signale les autres occurrences du même avertissement en tant qu’avertissements.</span><span class="sxs-lookup"><span data-stu-id="3e712-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="3e712-119">Par défaut, `/warnaserror-` est en vigueur, ce qui provoque les avertissements d’information uniquement.</span><span class="sxs-lookup"><span data-stu-id="3e712-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="3e712-120">Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e712-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="3e712-121">Si vous souhaitez que seuls certains avertissements spécifiques à traiter comme des erreurs, vous pouvez spécifier une liste séparée par des virgules des numéros d’avertissement à traiter comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3e712-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e712-122">Le `/warnaserror` option ne contrôle pas l’affichage des avertissements.</span><span class="sxs-lookup"><span data-stu-id="3e712-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="3e712-123">Utilisez le [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option pour désactiver les avertissements.</span><span class="sxs-lookup"><span data-stu-id="3e712-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="3e712-124">Pour définir /warnaserror pour traiter tous les avertissements comme des erreurs dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e712-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="3e712-125">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="3e712-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3e712-126">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3e712-126">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="3e712-127">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="3e712-127">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="3e712-128">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="3e712-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="3e712-129">3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3e712-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="3e712-130">4.  Vérifiez le **traiter tous les avertissements comme des erreurs** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="3e712-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="3e712-131">Pour définir /warnaserror à traiter certains avertissements comme des erreurs dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e712-131">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="3e712-132">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="3e712-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3e712-133">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3e712-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="3e712-134">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="3e712-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="3e712-135">3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3e712-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="3e712-136">4.  Assurez-vous que le **traiter tous les avertissements comme des erreurs** case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3e712-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="3e712-137">5.  Sélectionnez **erreur** à partir de la **Notification** colonne adjacente à l’avertissement qui doit être traitée comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="3e712-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e712-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e712-138">Example</span></span>  
 <span data-ttu-id="3e712-139">Le code suivant compile `In.vb` et indique au compilateur d’afficher une erreur pour la première occurrence de chaque avertissement rencontré.</span><span class="sxs-lookup"><span data-stu-id="3e712-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="3e712-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e712-140">Example</span></span>  
 <span data-ttu-id="3e712-141">Le code suivant compile `T2.vb` et traite uniquement l’avertissement pour les variables locales inutilisées (42024) comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="3e712-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e712-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e712-142">See Also</span></span>  
 [<span data-ttu-id="3e712-143">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e712-143">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3e712-144">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3e712-144">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="3e712-145">Configuration d’avertissements en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e712-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
