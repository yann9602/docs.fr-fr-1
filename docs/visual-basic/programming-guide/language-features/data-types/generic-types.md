---
title: "Types g&#233;n&#233;riques Visual Basic (Visual Basic) | Microsoft Docs"
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
  - "interfaces génériques"
  - "arguments de type de données, définition"
  - "délégués génériques"
  - "arguments (Visual Basic), types de données"
  - "Of (mot clé), utilisation"
  - "délégués génériques"
  - "contraintes, types génériques Visual Basic"
  - "paramètres génériques"
  - "paramètres de type de données"
  - "génériques, procédures"
  - "procédures génériques"
  - "types de données génériques (Visual Basic)"
  - "types de données (Visual Basic), comme paramètres"
  - "génériques (Visual Basic), types génériques"
  - "types de données (Visual Basic), comme arguments"
  - "classes génériques Visual Basic"
  - "paramètres, type"
  - "arguments de type"
  - "interfaces génériques"
  - "génériques (Visual Basic)"
  - "types génériques (Visual Basic)"
  - "paramètres génériques"
  - "structures génériques"
  - "génériques, classes"
  - "paramètres de type"
  - "arguments de type de données"
  - "structures génériques"
  - "paramètres, type de données"
  - "collections, génériques"
  - "classes génériques Visual Basic"
  - "paramètres de type de données, définition"
  - "arguments de type, définition"
  - "arguments (Visual Basic), type"
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Types g&#233;n&#233;riques Visual Basic (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Un *type générique* est un élément de programmation unique qui s’adapte pour exécuter la même fonction sur différents types de données. Quand vous définissez une classe ou procédure générique, vous n’avez pas besoin de définir une version distincte pour chaque type de données pour lequel vous voulez exécuter la fonction.  
  
 On pourrait comparer cet élément de programmation à un tournevis à têtes interchangeables. Vous examinez quel type de vis vous devez serrer et vous choisissez la tête de vis adaptée \(fendue, cruciforme, en étoile\). Quelle que soit la tête insérée dans le manche du tournevis, vous exécutez toujours la même fonction : vous serrez une vis.  
  
 ![Diagramme d'un tournevis défini en tant qu'outil générique](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Tournevis configuré comme un outil générique  
  
 Quand vous définissez un type générique, vous devez le paramétrer avec un ou plusieurs types de données. Cela permet au code utilisé d’adapter les types de données à ses besoins. Votre code peut déclarer plusieurs éléments de programmation différents à partir de l’élément générique, chacun d’eux agissant sur un ensemble différent de types de données. Ces éléments déclarés exécutent tous la même logique, quel que soit le type de données qu’ils utilisent.  
  
 Par exemple, vous pouvez créer et utiliser une classe « queue » qui agit sur un type de données spécifique, tel que `String`. Vous pouvez déclarer cette classe à partir de <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, comme indiqué dans l’exemple suivant.  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Vous pouvez maintenant utiliser `stringQ` pour agir uniquement sur des valeurs `String`. Étant donné que `stringQ` est spécifique aux valeurs `String` au lieu d’être généralisé pour les valeurs `Object`, aucune liaison tardive ou conversion de type n’est nécessaire. Cela permet de réduire le délai d’exécution et les erreurs d’exécution.  
  
 Pour plus d’informations sur l’utilisation d’un type générique, consultez [Comment : utiliser une classe générique](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## Exemple d’une classe générique  
 L’exemple suivant présente une définition squelette d’une classe générique.  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 Dans le squelette ci\-dessus, `t` est un *paramètre de type*, c’est\-à\-dire un espace réservé pour un type de données que vous fournissez quand vous déclarez la classe. Ailleurs dans votre code, vous pouvez déclarer des versions différentes de `classHolder` en fournissant différents types de données pour `t`. L’exemple suivant illustre deux déclarations.  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 Les instructions ci\-dessus déclarent des *classes construites*, dans lesquelles un type spécifique remplace le paramètre de type. Ce remplacement est propagé partout dans le code de la classe construite. L’exemple suivant montre à quoi ressemble la procédure `processNewItem` dans `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Pour un exemple plus complet, consultez [Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## Éléments de programmation disponibles  
 Vous pouvez définir et utiliser des délégués, structures, interfaces, procédures et classes génériques. Notez que [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] définit plusieurs classes, structures et interfaces génériques qui représentent les éléments génériques couramment utilisés. L’espace de noms <xref:System.Collections.Generic?displayProperty=fullName> fournit des dictionnaires, des listes, des files d’attente et des piles. Avant de définir votre propre élément générique, vérifiez s’il est disponible dans <xref:System.Collections.Generic?displayProperty=fullName>.  
  
 Les procédures ne sont pas des types, mais vous pouvez définir et utiliser des procédures génériques. Consultez [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## Avantages des types génériques  
 Un type générique sert de base de déclaration de plusieurs éléments de programmation différents, chacun agissant sur un type de données spécifique. À la place d’un type générique, vous pouvez utiliser :  
  
1.  un type unique pour le type de données `Object` ;  
  
2.  un ensemble de versions *spécifiques au type* du type de données, chaque version étant individuellement codée pour agir sur un type de données spécifique tel que `String`, `Integer` ou un type défini par l’utilisateur \(`customer`, par exemple\).  
  
 Un type générique présente les avantages suivants par rapport à ces alternatives :  
  
-   **Sécurité des types**. Avec les types génériques, une vérification des types est effectuée au moment de la compilation. Les types basés sur `Object` acceptent tous les types de données. Vous devez écrire le code permettant de vérifier si un type de données d’entrée est pris en charge. Avec les types génériques, le compilateur est capable d’identifier les incompatibilités de type avant l’exécution.  
  
-   **Performances**. Les types génériques ne nécessitent pas de conversion *boxing* et *unboxing* des données, car chacun d’eux est utilisé pour un type de données spécifique. Les opérations basées sur `Object` doivent effectuer une conversion boxing des types de données d’entrée pour les convertir en `Object` et effectuer une conversion unboxing des données de sortie. Les conversions boxing et unboxing réduisent les performances.  
  
     Les types basés sur `Object` sont également à liaison tardive, ce qui signifie que l’accès à leurs membres nécessite du code supplémentaire au moment de l’exécution. Cela réduit aussi les performances.  
  
-   **Consolidation du code**. Le code d’un type générique doit être défini une seule fois. Un ensemble de versions spécifiques au type d’un type de données doit répliquer le même code dans chaque version, la seule différence étant le type de données spécifique à cette version. Avec les types génériques, les versions spécifiques au type sont toutes générées à partir du type générique d’origine.  
  
-   **Réutilisation du code**. S’il est générique, le code qui ne dépend pas d’un type de données particulier peut être réutilisé avec divers types de données. Vous pouvez généralement le réutiliser même avec un type de données que vous n’avez pas prévu initialement.  
  
-   **Support de l’IDE**. Quand vous utilisez un type construit déclaré à partir d’un type générique, l’environnement de développement intégré \(IDE\) peut vous aider pendant le développement de votre code. Par exemple, IntelliSense vous indique les options spécifiques au type disponibles pour un argument d’une méthode ou d’un constructeur.  
  
-   **Algorithmes génériques**. Les types génériques sont conseillés pour les algorithmes abstraits qui sont indépendants du type. Par exemple, une procédure générique qui trie des éléments à l’aide de l’interface <xref:System.IComparable> peut être utilisée avec n’importe quel type de données implémentant <xref:System.IComparable>.  
  
## Contraintes  
 Dans la mesure du possible, le code d’une définition de type générique doit être indépendant du type. Toutefois, vous pouvez avoir besoin d’une fonction agissant sur tous les types de données fournis à votre type générique. Par exemple, si vous voulez comparer deux éléments pour les trier ou les classer, leur type de données doit implémenter l’interface <xref:System.IComparable>. Vous pouvez appliquer cette exigence en ajoutant une *contrainte* au paramètre de type.  
  
### Exemple de contrainte  
 L’exemple suivant présente une définition squelette d’une classe avec une contrainte qui exige que l’argument de type implémente <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Si du code tente ensuite de construire une classe de `itemManager` en fournissant un type qui n’implémente pas <xref:System.IComparable>, le compilateur signale une erreur.  
  
### Types de contraintes  
 Une contrainte peut spécifier les exigences suivantes dans n’importe quelle combinaison :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces.  
  
-   L’argument de type doit être du type d’une seule classe \(ou hériter de cette classe\).  
  
-   L’argument de type doit exposer un constructeur sans paramètre, accessible au code qui crée des objets à partir de celui\-ci.  
  
-   L’argument de type doit être un *type référence* ou un type *valeur*.  
  
 Si vous devez spécifier plusieurs contraintes, utilisez une *liste de contraintes* séparée par des virgules et mise entre accolades \(`{ }`\). Pour exiger un constructeur accessible, ajoutez le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) dans la liste. Pour exiger un type référence ou un type valeur, ajoutez le mot clé `Class` ou le mot clé `Structure`, respectivement.  
  
 Pour plus d’informations sur les contraintes, consultez [Type List](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### Exemple de liste de contraintes  
 L’exemple suivant présente une définition squelette d’une classe générique avec une liste de contraintes sur le paramètre de type. Dans le code qui crée une instance de cette classe, l’argument de type doit implémenter les deux interfaces <xref:System.IComparable> et <xref:System.IDisposable>, être un type référence et exposer un constructeur sans paramètre accessible.  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## Termes importants  
 La terminologie suivante s’applique aux types génériques :  
  
-   *Type générique*. Définition d’une classe, structure, interface, procédure ou délégué pour laquelle vous fournissez au moins un type de données lors de sa déclaration.  
  
-   *Paramètre de type*. Dans une définition de type générique, espace réservé pour un type de données que vous fournissez lors de la déclaration du type.  
  
-   *Argument de type*. Type de données spécifique qui remplace un paramètre de type quand vous déclarez un type construit à partir d’un type générique.  
  
-   *Contrainte*. Condition sur un paramètre de type qui restreint l’argument de type que vous pouvez lui fournir. Une contrainte peut exiger que l’argument de type implémente une interface particulière, soit ou hérite d’une classe particulière, contienne un constructeur sans paramètre accessible, ou soit un type référence ou un type valeur. Vous pouvez combiner ces contraintes, mais vous ne pouvez spécifier qu’une seule classe.  
  
-   *Type construit*. Classe, structure, interface, procédure ou délégué déclaré à partir d’un type générique en fournissant des arguments de type pour ses paramètres de type.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [As](../../../../visual-basic/language-reference/statements/as-clause.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)