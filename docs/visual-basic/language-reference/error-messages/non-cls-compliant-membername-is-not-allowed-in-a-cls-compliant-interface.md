---
title: "Non conforme CLS &lt;membername&gt; n’est pas autorisée dans une interface conforme CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
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
ms.openlocfilehash: 2861ef22c9307e5bd7d2eabf4f6e37bbd9086345
ms.lasthandoff: 03/13/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>Non conforme CLS &lt;membername&gt; n’est pas autorisée dans une interface conforme CLS
Une propriété, une procédure ou un événement dans une interface est marquée comme `<CLSCompliant(True)>` lorsque l’interface proprement dite est marquée comme `<CLSCompliant(False)>` ou n’est pas marquée.  
  
 Pour une interface conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), tous ses membres doivent être conformes.  
  
 Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute> Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute>  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40033  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous la conformité CLS et contrôlez le code source de l’interface, marquez l’interface comme `<CLSCompliant(True)>` si tous ses membres sont conformes.  
  
-   Si la conformité CLS et vous n’avez aucun contrôle sur le code source de l’interface, ou si elle n’est pas considérée comme conforme, définissez ce membre dans une autre interface.  
  
-   Si vous avez besoin que ce membre doit rester dans son interface actuelle, supprimez le <xref:System.CLSCompliantAttribute>à partir de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Voir aussi  
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
