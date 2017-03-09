---
title: "/warnaserror (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "warnaserror compiler option [Visual Basic]"
  - "/warnaserror compiler option [Visual Basic]"
  - "-warnaserror compiler option [Visual Basic]"
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /warnaserror (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Entraîne le compilateur à traiter la première occurrence d'un avertissement comme une erreur.  
  
## Syntaxe  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|\+ &#124; \-|Facultatif.  Par défaut, `/warnaserror-` est en vigueur, les avertissements n'empêchent pas le compilateur de générer un fichier de sortie.  Si vous utilisez l'option `/warnaserror` , qui est identique à `/warnaserror+`, les avertissements sont considérés comme des erreurs.|  
|`numberList`|Facultatif.  Liste délimitée par des virgules des numéros d'ID d'avertissement auxquels l'option `/warnaserror` s'applique.  Si aucun ID d'avertissement n'est spécifié, l'option `/warnaserror` s'applique à tous les avertissements.|  
  
## Notes  
 Avec l'option `/warnaserror`, tous les avertissements sont considérés comme des erreurs.  Ainsi, les messages qui normalement devraient être affichés en tant qu'avertissements apparaissent comme des erreurs.  Le compilateur signale les occurrences ultérieures du même avertissement en tant qu'avertissements.  
  
 Par défaut, `/warnaserror-` est en vigueur, ce qui engendre des avertissements de type informatif uniquement.  Si vous utilisez l'option `/warnaserror` , qui est identique à `/warnaserror+`, les avertissements sont considérés comme des erreurs.  
  
 Si vous souhaitez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules répertoriant les numéros d'avertissement à traiter comme des erreurs.  
  
> [!NOTE]
>  L'option `/warnaserror` ne contrôle pas l'affichage des avertissements.  Utilisez l'option [\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) pour désactiver des avertissements.  
  
||  
|-|  
|Pour définir \/warnaserror pour que tous les avertissements soient traités comme des erreurs dans l'IDE de Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Assurez\-vous que la case à cocher **Désactiver tous les avertissements** est désactivée.<br />4.  Activez la case à cocher **Considérer tous les avertissements comme des erreurs**.|  
  
||  
|-|  
|Pour définir \/warnaserror pour que les avertissements spécifiques soient traités comme des erreurs dans l'IDE de Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Assurez\-vous que la case à cocher **Désactiver tous les avertissements** est désactivée.<br />4.  Assurez\-vous que la case à cocher **Considérer tous les avertissements comme des erreurs** est désactivée.<br />5.  Sélectionnez **Erreur** dans la colonne **Notification** adjacente à l'avertissement qui doit être traité comme une erreur.|  
  
## Exemple  
 Le code suivant compile `In.vb` et demande au compilateur d'afficher une erreur pour la première occurrence de chaque avertissement rencontré :  
  
```  
vbc /warnaserror in.vb  
```  
  
## Exemple  
 Le code suivant compile `T2.vb` et les traite uniquement l'avertissement pour les variables locales inutilisées \(42024\) comme une erreur.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic)