---
title: "Activités d'expression régulière"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c04b5c97feb7843a5120e3b2171e132526caa961
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="1e22a-102">Activités d'expression régulière</span><span class="sxs-lookup"><span data-stu-id="1e22a-102">Regular Expression Activities</span></span>
<span data-ttu-id="1e22a-103">Cet exemple montre comment créer un ensemble d'activités qui exposent la fonctionnalité d'expression régulière de l'espace de noms <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="1e22a-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="1e22a-104">Ces activités personnalisées peuvent être utilisées dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="1e22a-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1e22a-105">expressions régulières, consultez [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="1e22a-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="1e22a-106">Le tableau suivant détaille les activités personnalisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="1e22a-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="1e22a-107">Activité</span><span class="sxs-lookup"><span data-stu-id="1e22a-107">Activity</span></span>|<span data-ttu-id="1e22a-108">Description</span><span class="sxs-lookup"><span data-stu-id="1e22a-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1e22a-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="1e22a-109">IsMatch</span></span>|<span data-ttu-id="1e22a-110">Spécifie si l'expression régulière a trouvé une correspondance dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="1e22a-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="1e22a-111">Correspondance</span><span class="sxs-lookup"><span data-stu-id="1e22a-111">Matches</span></span>|<span data-ttu-id="1e22a-112">Recherche une chaîne d'entrée pour toutes les occurrences d'une expression régulière et retourne toutes les correspondances réussies.</span><span class="sxs-lookup"><span data-stu-id="1e22a-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="1e22a-113">Remplacer</span><span class="sxs-lookup"><span data-stu-id="1e22a-113">Replace</span></span>|<span data-ttu-id="1e22a-114">Dans une chaîne d'entrée spécifiée, remplace les chaînes qui correspondent à un modèle d'expression régulière par une chaîne de remplacement spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1e22a-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="1e22a-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="1e22a-115">IsMatch</span></span>  
 <span data-ttu-id="1e22a-116">L'activité personnalisée `IsMatch` retourne la valeur `true` si la propriété de type chaîne `Input` trouve une correspondance dans l'expression régulière spécifiée dans la propriété `Pattern`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="1e22a-117">L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e22a-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="1e22a-118">Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `IsMatch`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="1e22a-119">Propriété ou valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-119">Property or Return Value</span></span>|<span data-ttu-id="1e22a-120">Description</span><span class="sxs-lookup"><span data-stu-id="1e22a-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="1e22a-121">Pattern (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-121">Pattern (required)</span></span>|<span data-ttu-id="1e22a-122">Expression régulière avec laquelle effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="1e22a-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="1e22a-123">Input (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-123">Input (required)</span></span>|<span data-ttu-id="1e22a-124">Chaîne d'entrée à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1e22a-124">The input string to search.</span></span>|  
|<span data-ttu-id="1e22a-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="1e22a-125">RegexOptions</span></span>|<span data-ttu-id="1e22a-126">Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1e22a-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="1e22a-127">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-127">Return value</span></span>|<span data-ttu-id="1e22a-128">`true` si l'entrée trouve une correspondance dans le modèle fourni ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="1e22a-129">L'exemple de code suivant montre comment utiliser l'activité personnalisée `IsMatch`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="1e22a-130">Correspondance</span><span class="sxs-lookup"><span data-stu-id="1e22a-130">Matches</span></span>  
 <span data-ttu-id="1e22a-131">L'activité personnalisée `Matches` recherche une chaîne d'entrée pour toutes les occurrences d'une expression régulière et retourne toutes les correspondances réussies.</span><span class="sxs-lookup"><span data-stu-id="1e22a-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="1e22a-132">L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e22a-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="1e22a-133">Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `IsMatch`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="1e22a-134">Propriété ou valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-134">Property or Return Value</span></span>|<span data-ttu-id="1e22a-135">Description</span><span class="sxs-lookup"><span data-stu-id="1e22a-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="1e22a-136">Pattern (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-136">Pattern (required)</span></span>|<span data-ttu-id="1e22a-137">Expression régulière avec laquelle effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="1e22a-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="1e22a-138">Input (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-138">Input (required)</span></span>|<span data-ttu-id="1e22a-139">Chaîne d'entrée à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1e22a-139">The input string to search.</span></span>|  
|<span data-ttu-id="1e22a-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="1e22a-140">RegexOptions</span></span>|<span data-ttu-id="1e22a-141">Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1e22a-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="1e22a-142">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-142">Return Value</span></span>|<span data-ttu-id="1e22a-143"><xref:System.Text.RegularExpressions.MatchCollection> qui contient la collection des correspondances réussies.</span><span class="sxs-lookup"><span data-stu-id="1e22a-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="1e22a-144">L'exemple de code suivant montre comment utiliser l'activité personnalisée `Matches`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="1e22a-145">Remplacer</span><span class="sxs-lookup"><span data-stu-id="1e22a-145">Replace</span></span>  
 <span data-ttu-id="1e22a-146">L'activité personnalisée `Replace` recherche une chaîne d'entrée et remplace toutes les chaînes qui correspondent à une expression régulière spécifiée par une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1e22a-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="1e22a-147">L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e22a-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="1e22a-148">Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `Replace`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="1e22a-149">Propriété ou valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-149">Property or Return Value</span></span>|<span data-ttu-id="1e22a-150">Description</span><span class="sxs-lookup"><span data-stu-id="1e22a-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="1e22a-151">Pattern (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-151">Pattern (required)</span></span>|<span data-ttu-id="1e22a-152">Expression régulière avec laquelle effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="1e22a-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="1e22a-153">Input (obligatoire)</span><span class="sxs-lookup"><span data-stu-id="1e22a-153">Input (required)</span></span>|<span data-ttu-id="1e22a-154">Chaîne d'entrée à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1e22a-154">The input string to search.</span></span>|  
|<span data-ttu-id="1e22a-155">Replacement</span><span class="sxs-lookup"><span data-stu-id="1e22a-155">Replacement</span></span>|<span data-ttu-id="1e22a-156">Chaîne de remplacement.</span><span class="sxs-lookup"><span data-stu-id="1e22a-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="1e22a-157">Si un `Replacement` est spécifié, la propriété `MatchEvaluator` est ignorée.</span><span class="sxs-lookup"><span data-stu-id="1e22a-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="1e22a-158">La propriété `Replacement` ou `MatchEvaluator` doit être définie.</span><span class="sxs-lookup"><span data-stu-id="1e22a-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="1e22a-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="1e22a-159">MatchEvaluator</span></span>|<span data-ttu-id="1e22a-160">Méthode personnalisée qui examine chaque correspondance et retourne la chaîne correspondante d'origine ou une chaîne de remplacement.</span><span class="sxs-lookup"><span data-stu-id="1e22a-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="1e22a-161">Si un `Replacement` est spécifié, la propriété `MatchEvaluator` est ignorée.</span><span class="sxs-lookup"><span data-stu-id="1e22a-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="1e22a-162">La propriété `Replacement` ou `MatchEvaluator` doit être définie.</span><span class="sxs-lookup"><span data-stu-id="1e22a-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="1e22a-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="1e22a-163">RegexOptions</span></span>|<span data-ttu-id="1e22a-164">Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1e22a-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="1e22a-165">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e22a-165">Return Value</span></span>|<span data-ttu-id="1e22a-166"><xref:System.Text.RegularExpressions.MatchCollection> qui contient la collection des correspondances réussies.</span><span class="sxs-lookup"><span data-stu-id="1e22a-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="1e22a-167">L'exemple de code suivant montre comment utiliser l'activité personnalisée `Replace`.</span><span class="sxs-lookup"><span data-stu-id="1e22a-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1e22a-168">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="1e22a-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="1e22a-169">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="1e22a-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1e22a-170">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="1e22a-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1e22a-171">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="1e22a-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e22a-172">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1e22a-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e22a-173">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1e22a-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e22a-174">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1e22a-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e22a-175">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1e22a-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`