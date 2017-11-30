---
title: Namespace, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a>Namespace, instruction
Déclare le nom d’un espace de noms et oblige le code source qui suit la déclaration à être compilé dans cet espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Composants  
 Global  
 Facultatif. Vous permet de définir un espace de noms en dehors de l’espace de noms racine de votre projet. Consultez [espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Obligatoire. Un nom unique qui identifie l’espace de noms. Doit être un identificateur Visual Basic valid. Pour plus d’informations, consultez [noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Facultatif. Éléments qui composent l’espace de noms. Cela inclut, mais ne sont pas limités à, énumérations, structures, interfaces, classes, modules, délégués et autres espaces de noms.  
  
 `End Namespace`  
 Met fin à une `Namespace` bloc.  
  
## <a name="remarks"></a>Remarques  
 Espaces de noms sont utilisés comme un système d’organisation. Ils permettent de classer et de présenter les éléments de programmation qui sont exposés à d’autres programmes et les applications. Notez qu’un espace de noms n’est pas un *type* dans le sens où une classe ou une structure, vous ne pouvez pas déclarer un élément de programmation comme ayant le type de données d’un espace de noms.  
  
 Tous les éléments de programmation déclarés après une `Namespace` instruction appartiennent à cet espace de noms. Visual Basic continue à compiler les éléments dans l’espace de noms déclaré dernière jusqu'à ce qu’il rencontre un `End Namespace` instruction ou une autre `Namespace` instruction.  
  
 Si un espace de noms est déjà définie, même en dehors de votre projet, vous pouvez ajouter des éléments de programmation à ce dernier. Pour ce faire, vous utilisez un `Namespace` instruction pour indiquer à Visual Basic pour compiler les éléments dans cet espace de noms.  
  
 Vous pouvez utiliser un `Namespace` instruction uniquement au niveau du fichier ou l’espace de noms. Cela signifie que la *contexte de déclaration* pour un espace de noms doit être un fichier source ou un autre espace de noms et qu’il ne peut pas être une classe, structure, module, interface ou une procédure. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Vous pouvez déclarer un espace de noms dans une autre. Il n’existe aucune limite stricte pour les niveaux d’imbrication, vous pouvez déclarer, mais rappelez-vous que tout autre code qui accède aux éléments déclarés dans l’espace de noms plus profond, elle doit utiliser une chaîne de qualification qui contient tous les noms d’espace de noms dans la hiérarchie d’imbrication.  
  
## <a name="access-level"></a>Niveau d’accès  
 Espaces de noms sont traités comme s’ils ont une `Public` niveau d’accès. Un espace de noms est accessible à partir du code n’importe où dans le même projet, à partir d’autres projets faisant référence au projet et à partir de tout assembly généré à partir du projet.  
  
 Les éléments de programmation déclarés au niveau de l’espace de noms, c'est-à-dire dans un espace de noms mais pas à l’intérieur d’un autre élément, peuvent avoir `Public` ou `Friend` accès. Si non spécifié, le niveau d’accès de cet élément prend `Friend` par défaut. Les éléments que vous pouvez déclarer au niveau de l’espace de noms incluent des classes, structures, modules, interfaces, énumérations et délégués. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Racine Namespace  
 Tous les noms d’espace de noms dans votre projet sont basés sur un *espace de noms racine*. Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet. Par exemple, si votre projet est nommé `Payroll`, ses éléments de programmation appartiennent à l’espace de noms `Payroll`. Si vous déclarez `Namespace funding`, le nom complet de cet espace de noms est `Payroll.funding`.  
  
 Si vous souhaitez spécifier un espace de noms dans un `Namespace` instruction, comme dans l’exemple de classe de liste générique, vous pouvez définir votre espace de noms racine à une valeur null. Pour ce faire, cliquez sur **propriétés du projet** à partir de la **projet** menu et puis désactivez la **espace de noms racine** entrée afin que la zone est vide. Si vous ne l’avez pas dans l’exemple de classe de liste générique, le compilateur Visual Basic prend `System.Collections.Generic` comme un espace de noms dans le projet `Payroll`, avec le nom complet du `Payroll.System.Collections.Generic`.  
  
 Vous pouvez également utiliser le `Global` (mot clé) pour faire référence à des éléments des espaces de noms définis à l’extérieur de votre projet. Cela vous permet de conserver le nom de votre projet en tant que l’espace de noms racine. Cela réduit le risque de fusion involontaire de vos éléments de programmation avec des espaces de noms existants. Pour plus d’informations, consultez la section « Global (mot clé) de noms qualifiés complets » dans [espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 Le `Global` mot clé peut également être utilisé dans une instruction Namespace. pour définir un espace de noms hors de l’espace de noms racine de votre projet. Pour plus d’informations, consultez la section « Mot clé Global dans instructions Namespace » dans [espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Résolution des problèmes.** L’espace de noms racine peut provoquer des concaténations inattendues des noms d’espace de noms. Si vous faites référence aux espaces de noms définis à l’extérieur de votre projet, le compilateur Visual Basic peut les interpréter comme des espaces de noms imbriqués dans l’espace de noms racine. Dans ce cas, le compilateur ne reconnaît pas les types qui ont déjà été définis dans les espaces de noms externe. Pour éviter ce problème, définissez votre espace de noms racine à une valeur null, comme décrit dans « Namespace racine », ou utiliser le `Global` mot clé pour accéder aux éléments des espaces de noms externe.  
  
## <a name="attributes-and-modifiers"></a>Attributs et les modificateurs  
 Vous ne pouvez pas appliquer des attributs à un espace de noms. Un attribut fournit des informations aux métadonnées de l’assembly, qui n’est pas significatif pour les classifieurs source tels que des espaces de noms.  
  
 Impossible d’appliquer l’accès ou les modificateurs de procédure ou d’autres modificateurs, à un espace de noms. Comme il n’est pas un type, ces modificateurs ne sont pas significatifs.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare deux espaces de noms, un imbriqué dans l’autre.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare plusieurs espaces de noms imbriqués sur une seule ligne, et elle est équivalente à l’exemple précédent.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant accède à la classe définie dans les exemples précédents.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit la structure d’une nouvelle classe de liste générique et l’ajoute à la <xref:System.Collections.Generic?displayProperty=nameWithType> espace de noms.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
