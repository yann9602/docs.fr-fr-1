---
title: "Nom de &lt;membername&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
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
ms.openlocfilehash: 6a678c66580a7917a3869aac81418152130debff
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nom de &lt;membername&gt; n’est pas conforme CLS
Un assembly est marqué comme `<CLSCompliant(True)>` , mais il expose un membre portant un nom qui commence par un trait de soulignement (`_`).  
  
 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais afin être conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il ne doit pas commencer par un trait de soulignement. Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute> Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute>  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40031  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous avez un contrôle sur le code source, modifiez le nom du membre afin qu’il ne commence pas par un trait de soulignement.  
  
-   Si vous avez besoin que le nom de membre reste inchangé, supprimez le <xref:System.CLSCompliantAttribute>à partir de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute> Vous pouvez toujours marquer l’assembly comme `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
