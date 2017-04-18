---
title: "&lt;proceduresignature1&gt; n’est pas conforme CLS, car il surcharge &lt;proceduresignature2&gt; dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
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
ms.openlocfilehash: 984c04a107444036b980439b231d27a8a81656c1
ms.lasthandoff: 03/13/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; n’est pas conforme CLS, car il surcharge &lt;proceduresignature2&gt; dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau
Une procédure ou une propriété est marquée en tant que `<CLSCompliant(True)>` lorsqu’elle substitue une autre procédure ou propriété et la seule différence entre leurs listes de paramètres est le niveau d’imbrication d’un tableau en escalier ou le rang d’un tableau.  
  
 Dans les déclarations suivantes, les deuxième et troisième déclarations génèrent cette erreur.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 La deuxième déclaration remplace le paramètre unidimensionnel d’origine `arrayParam` à un tableau de tableaux. La troisième déclaration remplace `arrayParam` un tableau à deux dimensions (rang 2). Bien que Visual Basic autorise les surcharges à différer uniquement par une de ces modifications, une telle surcharge n’est pas conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute> Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute>  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40035  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous avez besoin de la conformité CLS, définissez vos surcharges pour diffèrent autrement que seules les modifications mentionnées dans cette page d’aide.  
  
-   Si vous avez besoin que les surcharges diffèrent uniquement par les modifications mentionnées dans l’aide de cette page, supprimez le <xref:System.CLSCompliantAttribute>à partir de leurs définitions ou marquez-les comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Voir aussi  
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Surcharges](../../../visual-basic/language-reference/modifiers/overloads.md)
