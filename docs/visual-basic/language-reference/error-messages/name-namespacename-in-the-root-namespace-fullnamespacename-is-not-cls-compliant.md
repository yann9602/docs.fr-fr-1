---
title: "Nom de &lt;namespacename&gt; dans l’espace de noms racine &lt;fullnamespacename&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
dev_langs:
- VB
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
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
ms.openlocfilehash: 344a0ca098160a8d9f5bc8281a941311f82000c4
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>Nom de &lt;namespacename&gt; dans l’espace de noms racine &lt;fullnamespacename&gt; n’est pas conforme CLS
Un assembly est marqué comme `<CLSCompliant(True)>`, mais un élément de l’espace de noms racine commence par un trait de soulignement (`_`).  
  
 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais afin être conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il ne doit pas commencer par un trait de soulignement. Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute> Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute>  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40039  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous avez besoin de la conformité CLS, modifiez le nom d’espace de noms racine afin qu’aucun de ses éléments ne commence par un trait de soulignement.  
  
-   Si vous avez besoin que l’espace de noms reste inchangé, supprimez le <xref:System.CLSCompliantAttribute>à partir de l’assembly ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [/RootNamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)   
 [Page Application, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
