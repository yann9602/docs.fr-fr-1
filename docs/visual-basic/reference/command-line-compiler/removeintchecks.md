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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e50200b8755ccc6b1c173024856955f5075b67e
ms.lasthandoff: 03/13/2017

---
# <a name="removeintchecks"></a>/removeintchecks
Active la vérification des opérations d’entiers ou d’erreur de dépassement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. La `/removeintchecks-` option, le compilateur à vérifier tous les calculs d’entier pour les erreurs de dépassement de capacité. La valeur par défaut est `/removeintchecks-`.<br /><br /> Spécification de `/removeintchecks` ou `/removeintchecks+` empêche la vérification des erreurs et peuvent effectuer des calculs d’entier plus rapides. Toutefois, sans vérification des erreurs, et si les capacités de type données sont dépassées, des résultats incorrects peuvent être stockées sans le déclenchement d’une erreur.|  
  
|Pour définir /removeintchecks dans Visual Studio environnement de développement intégré|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Cliquez sur le bouton **Avancées** .<br />4.  Modifiez la valeur de la **supprimer les contrôles de dépassement de capacité d’entier** boîte.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement d’entier.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
