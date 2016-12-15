---
title: "Namespace Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Namespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "namespaces, root"
  - "Namespace statement"
  - "namespaces, nested"
  - "declaring namespaces, syntax"
  - "namespaces, declaring"
  - "root namespaces"
  - "declarations, namespaces"
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare le nom d'un espace de noms et provoque la compilation du code source qui suit la déclaration dans cet espace de noms.  
  
## Syntaxe  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## Composants  
 Global  
 Facultatif.  Vous permet de définir un espace de noms hors de l'espace de noms racine de votre projet.  Consultez [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Obligatoire.  Nom univoque d'identification de l'espace de noms.  Doit être un identificateur Visual Basic valide.  Pour plus d'informations, consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Facultatif.  Éléments qui composent l'espace de noms.  Ceux\-ci incluent, mais n'est pas limitée à, des énumérations, des structures, des interfaces, des classes, des modules, des délégués, et d'autres espaces de noms.  
  
 `End Namespace`  
 Met fin à un bloc `Namespace`.  
  
## Notes  
 Les espaces de noms sont utilisés comme un système d'organisation.  Ils permettent de classer et de présenter des éléments de programmation exposés à d'autres programmes et applications.  notez qu'un espace de noms n'est pas un *type* dans le sens qu'une classe ou ne vous structure pas être\-ne peut pas déclarer un élément de programmation pour avoir le type de données d'un espace de noms.  
  
 Tous les éléments de programmation déclarés après une instruction `Namespace` appartiennent à cet espace de noms.  Visual Basic continue à compiler les éléments dans le dernier espace de noms déclaré jusqu'à ce qu'il rencontre une instruction `End Namespace` ou une autre instruction `Namespace`.  
  
 Si un espace de noms est déjà défini, même à l'extérieur de votre projet, vous pouvez y ajouter des éléments de programmation.  Pour ce faire, vous utilisez une instruction d' `Namespace` pour exécuter Visual Basic pour compiler des éléments dans cet espace de noms.  
  
 Vous pouvez utiliser une instruction `Namespace` uniquement au niveau du fichier ou de l'espace de noms.  Cela signifie que le *contexte de déclaration* pour un espace de noms doit être un fichier source ou un autre espace de noms, et ne peut pas être une classe, une structure, un module, une interface ou une procédure.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Vous pouvez déclarer un espace de noms dans un autre.  Aucune limite stricte n'est appliquée aux niveaux d'imbrication que vous pouvez déclarer, mais n'oubliez pas qu'e tout autre code qui accède aux éléments déclarés dans l'espace de noms le plus profond doit utiliser une chaîne de qualification qui contient tout les noms d'espace de noms dans la hiérarchie d'imbrication.  
  
## Niveau d'accès  
 Les espaces de noms sont traités comme s'ils ont un niveau d'accès d' `Public` .  Un espace de noms peut être accessible à partir du code depuis n'importe quel emplacement dans le même projet, dans d'autres projets qui référencent le projet et dans un assembly généré à partir du projet.  
  
 Les éléments de programmation déclarés au niveau de l'espace de noms, c'est\-à\-dire dans un espace de noms mais pas à l'intérieur d'un autre élément, peuvent disposer d'un accès `Public` ou `Friend`.  S'il n'est pas spécifié, le niveau d'accès de cet élément prend par défaut la valeur `Friend`.  Les éléments que vous pouvez déclarer au niveau de l'espace de noms sont les classes, structures, modules, interfaces, énumérations et délégués.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## L'espace de noms racine  
 Tous les espaces de noms contenus dans votre projet sont basés sur un *espace de noms racine*.  Visual Studio assigne votre nom de projet en tant qu'espace de noms racine par défaut pour l'ensemble du code de votre projet.  Par exemple, si votre projet est nommé `Payroll`, ses éléments de programmation appartiennent à l'espace de noms `Payroll`.  Si vous déclarez `Namespace funding`, le nom complet de cet espace de noms est `Payroll.funding`.  
  
 Si vous souhaitez spécifier un espace de noms existant dans une instruction `Namespace`, comme dans l'exemple de classe de liste générique, vous pouvez affecter une valeur null à votre espace de noms racine.  Pour ce faire, cliquez sur **Propriétés du projet** dans le menu **Projet**, puis supprimez l'entrée **Espace de noms racine** afin que la zone soit vide.  Si vous ne le faites pas dans l'exemple de classe de liste générique, le compilateur Visual Basic prend `System.Collections.Generic` comme nouvel espace de noms dans le projet `Payroll`, avec le nom complet `Payroll.System.Collections.Generic`.  
  
 Vous pouvez également utiliser le mot clé `Global` pour faire référence aux éléments des espaces de noms définis à l'extérieur de votre projet.  Cela vous permet de conserver votre nom de projet comme espace de noms racine.  Cela réduit également le risque de fusion involontaire de vos éléments de programmation avec ceux des espaces de noms existants.  Pour plus d'informations, consultez « mot clé global la section de noms qualifiés complets » dans [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 le mot clé d' `Global` peut également être utilisé dans une instruction de l'espace de noms.  Cela vous permet de définir un espace de noms hors de l'espace de noms racine de votre projet.  Pour plus d'informations, consultez « mot clé global la section de l'espace de noms instructions » dans [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **résoudre.** L'espace de noms racine peut provoquer des concaténations inattendues des noms d'espace de noms.  Si vous créez une référence aux espaces de noms définis à l'extérieur de votre projet, le compilateur Visual Basic peut les interpréter comme des espaces de noms imbriqués dans votre espace de noms racine.  Dans ce cas, le compilateur ne reconnaît pas les types qui ont déjà été définis dans les espaces de noms externes.  Pour éviter ceci, définit l'espace de noms racine à une valeur NULL comme décrit dans « espace de noms racine, » ou utilise le mot clé d' `Global` pour accéder aux éléments des espaces de noms externes.  
  
## Attributs et modificateurs  
 Vous ne pouvez pas appliquer d'attributs à un espace de noms.  Un attribut fournit des informations aux métadonnées de l'assembly, qui ne sont pas explicites pour les classifieurs source tels que les espaces de noms.  
  
 Vous ne pouvez pas appliquer de modificateurs d'accès ou de procédure, ou d'autres modificateurs, à un espace de noms.  L'espace de noms n'étant pas un type, ces modificateurs ne sont pas explicites.  
  
## Exemple  
 L'exemple suivant déclare deux espaces de noms, l'un imbriqué dans l'autre.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant déclare plusieurs espaces de noms imbriqués sur une seule ligne, et est équivalent à l'exemple précédent.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## Exemple  
 L'exemple suivant accède à la classe définie dans les précédents exemples.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## Exemple  
 L'exemple suivant définit la structure d'une nouvelle classe de liste générique et l'ajoute à l'espace de noms <xref:System.Collections.Generic?displayProperty=fullName>.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)