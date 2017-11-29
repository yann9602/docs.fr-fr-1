---
title: "&#39; &lt;classname&gt;&#39; n’est pas conforme CLS, car l’interface &#39;&lt; InterfaceName&gt;&#39; il implémente n’est pas conforme CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7bad6aa4c8fa9979824766e83aba75697d6e98d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39; &lt;classname&gt;&#39; n’est pas conforme CLS, car l’interface &#39;&lt; InterfaceName&gt;&#39; il implémente n’est pas conforme CLS
Une classe ou une interface est marquée comme `<CLSCompliant(True)>` quand elle est dérivée d’un type ou implémente un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.  
  
 Pour une classe ou une interface soit conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), sa hiérarchie d’héritage entière doit être conforme. Cela signifie que chaque type dont elle hérite, directement ou indirectement, doit être conforme. De même, si une classe implémente une ou plusieurs interfaces, celles-ci doivent toutes être conformes au sein de leurs hiérarchies d’héritage.  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40029  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si la conformité CLS est obligatoire, définissez ce type dans une autre hiérarchie d’héritage ou dans un autre schéma d’implémentation.  
  
-   Si le type doit rester au sein de sa hiérarchie d’héritage ou de son schéma d’implémentation actuels, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Voir aussi  
 [\<PAVE sur > écriture d’un Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
