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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77968872d878f7b4d6b0eb3f27516a75abb54919
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="regular-expression-activities"></a>Activités d'expression régulière
Cet exemple montre comment créer un ensemble d'activités qui exposent la fonctionnalité d'expression régulière de l'espace de noms <xref:System.Text.RegularExpressions>. Ces activités personnalisées peuvent être utilisées dans une application de workflow. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]expressions régulières, consultez [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 Le tableau suivant détaille les activités personnalisées dans cet exemple.  
  
|Activité|Description|  
|--------------|-----------------|  
|IsMatch|Spécifie si l'expression régulière a trouvé une correspondance dans la chaîne d'entrée.|  
|Correspondance|Recherche une chaîne d'entrée pour toutes les occurrences d'une expression régulière et retourne toutes les correspondances réussies.|  
|Remplacer|Dans une chaîne d'entrée spécifiée, remplace les chaînes qui correspondent à un modèle d'expression régulière par une chaîne de remplacement spécifiée.|  
  
## <a name="ismatch"></a>IsMatch  
 L'activité personnalisée `IsMatch` retourne la valeur `true` si la propriété de type chaîne `Input` trouve une correspondance dans l'expression régulière spécifiée dans la propriété `Pattern`. L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>.  
  
 Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `IsMatch`.  
  
|Propriété ou valeur de retour|Description|  
|------------------------------|-----------------|  
|Pattern (obligatoire)|Expression régulière avec laquelle effectuer la recherche.|  
|Input (obligatoire)|Chaîne d'entrée à rechercher.|  
|RegexOptions|Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.|  
|Valeur de retour|`true` si l'entrée trouve une correspondance dans le modèle fourni ; sinon `false`.|  
  
 L'exemple de code suivant montre comment utiliser l'activité personnalisée `IsMatch`.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Correspondance  
 L'activité personnalisée `Matches` recherche une chaîne d'entrée pour toutes les occurrences d'une expression régulière et retourne toutes les correspondances réussies. L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A>.  
  
 Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `IsMatch`.  
  
|Propriété ou valeur de retour|Description|  
|------------------------------|-----------------|  
|Pattern (obligatoire)|Expression régulière avec laquelle effectuer la recherche.|  
|Input (obligatoire)|Chaîne d'entrée à rechercher.|  
|RegexOptions|Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.|  
|Valeur de retour|<xref:System.Text.RegularExpressions.MatchCollection> qui contient la collection des correspondances réussies.|  
  
 L'exemple de code suivant montre comment utiliser l'activité personnalisée `Matches`.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Remplacer  
 L'activité personnalisée `Replace` recherche une chaîne d'entrée et remplace toutes les chaînes qui correspondent à une expression régulière spécifiée par une chaîne. L'activité dérive de <xref:System.Activities.CodeActivity%601> et, dans la méthode <xref:System.Activities.CodeActivity%601.Execute%2A>, appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A>.  
  
 Le tableau suivant décrit les propriétés et la valeur de retour pour l'activité personnalisée `Replace`.  
  
|Propriété ou valeur de retour|Description|  
|------------------------------|-----------------|  
|Pattern (obligatoire)|Expression régulière avec laquelle effectuer la recherche.|  
|Input (obligatoire)|Chaîne d'entrée à rechercher.|  
|Replacement|Chaîne de remplacement.<br /><br /> Si un `Replacement` est spécifié, la propriété `MatchEvaluator` est ignorée. La propriété `Replacement` ou `MatchEvaluator` doit être définie.|  
|MatchEvaluator|Méthode personnalisée qui examine chaque correspondance et retourne la chaîne correspondante d'origine ou une chaîne de remplacement.<br /><br /> Si un `Replacement` est spécifié, la propriété `MatchEvaluator` est ignorée. La propriété `Replacement` ou `MatchEvaluator` doit être définie.|  
|RegexOptions|Combinaison d’opérations OR [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valeurs d’énumération.|  
|Valeur de retour|<xref:System.Text.RegularExpressions.MatchCollection> qui contient la collection des correspondances réussies.|  
  
 L'exemple de code suivant montre comment utiliser l'activité personnalisée `Replace`.  
  
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
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution RegexActivities.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`