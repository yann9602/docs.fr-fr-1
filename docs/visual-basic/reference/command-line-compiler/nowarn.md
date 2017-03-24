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
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 61b145a9eb95f5357c7aa2983a96c31e8f2cef6a
ms.lasthandoff: 03/13/2017

---
# <a name="nowarn"></a>/nowarn
Supprime la capacité du compilateur à générer des avertissements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`numberList`|Facultatif. Liste délimitée par des virgules des numéros d’identification avertissement que le compilateur doit supprimer. Si l’ID d’avertissement ne sont spécifié, tous les avertissements sont supprimés.|  
  
## <a name="remarks"></a>Notes  
 La `/nowarn` option, le compilateur ne génère ne pas les avertissements. Pour supprimer un avertissement, fournissez l’ID d’avertissement pour la `/nowarn` option suit le signe deux-points. Séparez plusieurs numéros d’avertissement par des virgules.  
  
 Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement. Par exemple, si vous souhaitez supprimer BC42024, numéro d’avertissement pour les variables locales inutilisées, spécifiez `/nowarn:42024`.  
  
 Pour plus d’informations sur les numéros d’avertissement, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Pour définir /nowarn dans Visual Studio environnement de développement intégré|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Sélectionnez le **désactiver tous les avertissements** case à cocher pour désactiver tous les avertissements.<br />     ou<br />     Pour désactiver un avertissement particulier, cliquez sur **aucun** dans la liste déroulante adjacente à l’avertissement.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche pas d’avertissements.  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche pas les avertissements pour les variables locales inutilisées (42024).  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
