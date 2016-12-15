---
title: "Imports Statement (.NET Namespace and Type) | Microsoft Docs"
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
  - "vb.Imports"
  - "imports"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared element names [Visual Basic], qualification"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "aliases [Visual Basic], Imports statement"
  - "container elements [Visual Basic]"
  - "namespaces [Visual Basic], importing"
  - "Imports statement [Visual Basic], syntax"
  - "import aliases [Visual Basic]"
  - "aliases [Visual Basic], import"
  - "declared elements [Visual Basic], container elements"
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports Statement (.NET Namespace and Type)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permet le référencement des noms de types sans qualification d'espace de noms.  
  
## Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`aliasname`|Facultatif.  *Alias d'importation* ou nom par lequel le code peut faire référence à `namespace` au lieu de la chaîne de qualification complète.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Obligatoire.  Nom qualifié complet de l'espace de noms importé.  Il peut s'agir d'une chaîne d'espaces de noms imbriqués à un niveau quelconque.|  
|`element`|Facultatif.  Nom d'un élément de programmation déclaré dans l'espace de noms.  Il peut s'agir de n'importe quel élément conteneur.|  
  
## Notes  
 L'instruction `Imports`  permet le référencement direct des types contenus dans un espace de noms donné.  
  
 Vous pouvez fournir un nom d'espace de noms unique ou une chaîne d'espaces de noms imbriqués.  Chaque espace de noms imbriqué est séparé de l'espace de noms du niveau supérieur suivant par un point \(`.`\), comme l'exemple suivant l'illustre.  
  
 `Imports System.Collections.Generic`  
  
 Chaque fichier source peut contenir un nombre quelconque d'instructions `Imports`.  Celles\-ci doivent suivre les déclarations d'option telles que l'instruction `Option Strict`, et elles doivent précéder les déclarations d'élément de programmation telles que les instructions `Module` ou `Class`.  
  
 Vous pouvez utiliser `Imports` seulement au niveau du fichier.  Cela signifie que le contexte de déclaration pour l'importation doit être un fichier source, et ne peut pas être un espace de noms, une classe, une structure, un module, une interface, une procédure ou un bloc.  
  
 Notez que l'instruction `Imports` ne rend pas d'éléments d'autres projets et assemblys disponibles à votre projet.  L'importation ne prend pas la place de la définition d'une référence.  Elle rend inutile la qualification des noms qui sont déjà disponibles pour votre projet.  Pour plus d'informations, consultez « Importation d'éléments conteneurs » dans [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Vous pouvez définir des instructions implicites `Imports` en utilisant le [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md).  
  
## Alias d'importation  
 Un nouvel *alias d'importation* définit l'alias pour un espace de noms ou un type.  Les alias d'importation sont utiles lorsque vous devez utiliser des éléments portant le même nom et qui sont déclarés dans un ou plusieurs espaces de noms.  Pour plus d'informations et pour obtenir un exemple, consultez « Qualification d'un nom d'élément » dans [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Vous ne devez pas déclarer de membre au niveau du module avec le même nom que `aliasname`.  Sinon, le compilateur Visual Basic utilise uniquement `aliasname` pour le membre déclaré et ne le reconnaît plus comme alias d'importation.  
  
 Bien que la syntaxe utilisée pour déclarer un alias d'importation soit similaire à celle utilisée pour importer un préfixe d'espace de noms XML, les résultats sont différents.  Un alias d'importation peut être utilisé comme une expression dans le code, alors qu'un préfixe d'espace de noms XML peut être utilisé uniquement dans les littéraux XML ou les propriétés d'axe XML comme préfixe pour un élément qualifié ou nom de l'attribut.  
  
### Noms d'éléments  
 Si vous fournissez `element`, il doit représenter un *élément conteneur*, c'est\-à\-dire un élément de programmation qui peut contenir d'autres éléments.  Les éléments conteneurs comprennent des classes, structures, modules, interfaces et énumérations.  
  
 La portée des éléments mis à disposition par une instruction `Imports` varie selon que vous spécifiez `element`.  Si vous spécifiez uniquement `namespace`, tous les membres à nom unique de cet espace de noms ainsi que les membres des éléments conteneurs présents dans cet espace de noms, sont disponibles sans qualification.  Si vous spécifiez `namespace` et `element`, seuls les membres de cet élément sont disponibles sans qualification.  
  
## Exemple  
 L'exemple suivant retourne tous les dossiers dans le répertoire C:\\ à l'aide de la classe <xref:System.IO.DirectoryInfo>.  
  
 Le code n'a aucune instruction `Imports` en haut du fichier.  Par conséquent, les références `DirectoryInfo`, <xref:System.Text.StringBuilder> et <xref:Microsoft.VisualBasic.ControlChars.CrLf> sont entièrement qualifiées avec les espaces de noms.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## Exemple  
 L'exemple suivant inclut des instructions `Imports` pour les espaces de noms référencés.  Par conséquent, les types n'ont pas à être entièrement qualifiés avec les espaces de noms.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## Exemple  
 L'exemple suivant inclut des instructions `Imports` qui créent des alias pour les espaces de noms référencés.  Les types sont qualifiés avec les alias.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## Exemple  
 L'exemple suivant inclut des instructions `Imports` qui créent des alias pour les types référencés.  Alias utilisés pour spécifier les types.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## Voir aussi  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)