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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28f232b1ad8200455550f2f4c1204818c8b143ab
ms.lasthandoff: 03/13/2017

---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
Entraîne le compilateur à traiter la première occurrence d’un avertissement comme une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|+ &#124; -|Facultatif. Par défaut, `/warnaserror-` est en vigueur, les avertissements n’empêchent pas le compilateur de générer un fichier de sortie. Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.|  
|`numberList`|Facultatif. Liste délimitée par des virgules l’ID d’avertissement numéros auquel la `/warnaserror` option s’applique. Si aucun ID d’avertissement n’est spécifié, la `/warnaserror` option s’applique à tous les avertissements.|  
  
## <a name="remarks"></a>Remarques  
 La `/warnaserror` option considère tous les avertissements comme des erreurs. Tous les messages qui normalement devraient être affichés comme avertissements apparaissent comme des erreurs. Le compilateur signale les occurrences ultérieures du même avertissement en tant qu’avertissements.  
  
 Par défaut, `/warnaserror-` est en vigueur, ce qui provoque les avertissements d’information uniquement. Le `/warnaserror` option, qui est le même que `/warnaserror+`, génère des avertissements à traiter comme des erreurs.  
  
 Si vous souhaitez que seuls certains avertissements spécifiques à traiter comme des erreurs, vous pouvez spécifier une liste séparée par des virgules des numéros d’avertissement à traiter comme des erreurs.  
  
> [!NOTE]
>  La `/warnaserror` option ne contrôle pas l’affichage des avertissements. Utilisez le [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option pour désactiver les avertissements.  
  
|Pour définir /warnaserror pour traiter tous les avertissements comme des erreurs dans l’IDE de Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.<br />4.  Vérifier la **traiter tous les avertissements comme des erreurs** case à cocher.|  
  
|Pour définir /warnaserror pour traiter les avertissements spécifiques comme des erreurs dans l’IDE de Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**.<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Assurez-vous que le **désactiver tous les avertissements** case à cocher est désactivée.<br />4.  Assurez-vous que le **traiter tous les avertissements comme des erreurs** case à cocher est désactivée.<br />5.  Sélectionnez **erreur** à partir de la **Notification** colonne adjacente à l’avertissement qui doit être traitée comme une erreur.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et demande au compilateur d’afficher une erreur pour la première occurrence de chaque avertissement rencontré.  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et traite uniquement l’avertissement pour les variables locales inutilisées (42024) comme une erreur.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
