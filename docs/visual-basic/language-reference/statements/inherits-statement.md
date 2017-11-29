---
title: Inherits Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae9ba54c3fd1ec3332c9f6260bc19a1293270ad8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="inherits-statement"></a>Inherits Statement
Provoque la classe en cours ou interface hérite des attributs, variables, propriétés, procédures et événements d’une autre classe ou ensemble d’interfaces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`basetypenames`|Obligatoire. Le nom de la classe à partir de laquelle cette classe dérive.<br /><br /> ou<br /><br /> Les noms des interfaces à partir duquel cette interface dérive. Utilisez des virgules pour séparer plusieurs noms.|  
  
## <a name="remarks"></a>Remarques  
 Si utilisé, la `Inherits` instruction doit être la première ligne non vide et sans commentaire dans une définition de classe ou interface. Elle doit suivre immédiatement le `Class` ou `Interface` instruction.  
  
 Vous pouvez utiliser `Inherits` uniquement dans une classe ou interface. Cela signifie que le contexte de déclaration pour un héritage ne peut pas être un fichier source, espace de noms, structure, module, procédure ou bloc.  
  
## <a name="rules"></a>Règles  
  
-   **Héritage de classe.** Si une classe utilise le `Inherits` instruction, vous pouvez spécifier qu’une seule classe de base.  
  
     Une classe ne peut pas hériter d’une classe imbriquée.  
  
-   **Héritage de l’interface.** Si une interface utilise les `Inherits` instruction, vous pouvez spécifier une ou plusieurs interfaces de base. Vous pouvez hériter de deux interfaces même si chacune définit un membre portant le même nom. Si vous procédez ainsi, le code d’implémentation doit utiliser qualification de noms pour spécifier le membre qu’il implémente.  
  
     Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif. Par exemple, un `Public` interface ne peut pas hériter d’un `Friend` interface.  
  
     Une interface ne peut pas hériter d’une interface imbriquée dans celui-ci.  
  
 Un exemple d’héritage de classe dans le .NET Framework est la <xref:System.ArgumentException> (classe), qui hérite de la <xref:System.SystemException> classe. Cela fournit à <xref:System.ArgumentException> toutes les propriétés prédéfinies et les procédures requises par les exceptions système, telles que la <xref:System.Exception.Message%2A> propriété et la <xref:System.Exception.ToString%2A> (méthode).  
  
 Un exemple d’héritage d’interface dans le .NET Framework est la <xref:System.Collections.ICollection> interface qui hérite de la <xref:System.Collections.IEnumerable> interface. Cela provoque une <xref:System.Collections.ICollection> d’hériter de la définition de l’énumérateur permettant de parcourir une collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Inherits` instruction pour montrer comment une classe nommée `thisClass` peut hériter de tous les membres d’une classe de base nommée `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’héritage de plusieurs interfaces.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 L’interface nommée `thisInterface` inclut désormais toutes les définitions de la <xref:System.IComparable>, <xref:System.IDisposable>, et <xref:System.IFormattable> interfaces, les membres hérités fournissent respectivement de comparaison spécifique au type de deux objets, libérer les ressources allouées. et d’exprimer la valeur d’un objet comme un `String`. Une classe qui implémente `thisInterface` doit implémenter chaque membre de chaque interface de base.  
  
## <a name="see-also"></a>Voir aussi  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
