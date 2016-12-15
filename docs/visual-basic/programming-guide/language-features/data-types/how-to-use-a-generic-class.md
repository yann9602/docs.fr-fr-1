---
title: "Comment&#160;: utiliser une classe g&#233;n&#233;rique (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "paramètres de type, définition"
  - "arguments de type de données, définition"
  - "arguments (Visual Basic), types de données"
  - "Of (mot clé), utilisation"
  - "paramètres génériques"
  - "paramètres de type de données"
  - "génériques (Visual Basic), à propos des génériques"
  - "types de données (Visual Basic), comme paramètres"
  - "types de données (Visual Basic), comme arguments"
  - "paramètres, type"
  - "types génériques (Visual Basic)"
  - "paramètres génériques"
  - "génériques (Visual Basic), création de types génériques"
  - "arguments de type de données"
  - "paramètres, type de données"
  - "paramètres de type de données, définition"
  - "arguments de type, définition"
  - "arguments (Visual Basic), type"
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: utiliser une classe g&#233;n&#233;rique (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une classe qui accepte des *paramètres de type* est appelée *classe générique*. Si vous utilisez une classe générique, vous pouvez générer une *classe construite* à partir de celle-ci en fournissant un *argument de type* pour chacun de ces paramètres. Vous pouvez ensuite déclarer une variable du type classe construite, et vous pouvez créer une instance de la classe construite et l’assigner à cette variable.  
  
 En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.  
  
 La procédure suivante prend une classe générique définie dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] et crée une instance à partir d’elle.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Pour utiliser une classe qui prend un paramètre de type  
  
1.  Au début de votre fichier source, incluez une [instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer l’espace de noms <xref:System.Collections.Generic?displayProperty=fullName>. Cette opération vous permet de référencer la classe <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> sans avoir à la qualifier pleinement pour la différencier des autres classes de file d’attente, comme <xref:System.Collections.Queue?displayProperty=fullName>.  
  
2.  Créez l’objet de façon normale, mais ajoutez `(Of` `type``)` juste après le nom de la classe.  
  
     L’exemple suivant utilise la même classe (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) pour créer deux objets de file d’attente qui contiennent des éléments de différents types de données. Il ajoute des éléments à la fin de chaque file d’attente, puis supprime et affiche les éléments du début de chaque file d’attente.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Comment : définir une classe qui peut fournir des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)