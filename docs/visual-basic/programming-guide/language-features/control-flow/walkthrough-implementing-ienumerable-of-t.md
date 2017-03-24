---
title: "Implémentation d’IEnumerable en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures, optimizing performance
- control flow
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
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
ms.openlocfilehash: 68c37c46cbceb1056d50972cdc58ddb7c7577447
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Procédure pas à pas : implémentation d'IEnumerable(Of T) en Visual Basic
Le <xref:System.Collections.Generic.IEnumerable%601>interface est implémentée par les classes qui peuvent retourner une séquence de valeurs élément par élément à la fois.</xref:System.Collections.Generic.IEnumerable%601> L’avantage de renvoyer des données d’un élément à la fois est que vous n’avez pas à charger l’ensemble complet des données en mémoire pour l’utiliser. Vous devez uniquement utiliser la mémoire nécessaire au chargement d’un élément unique à partir des données. Classes qui implémentent la `IEnumerable(T)` interface peut être utilisée avec `For Each` boucles ou les requêtes LINQ.  
  
 Par exemple, considérez une application qui doit lire un fichier texte volumineux et retourner chaque ligne du fichier qui correspond aux critères de recherche particuliers. L’application utilise une requête LINQ pour retourner les lignes à partir du fichier qui correspondent aux critères spécifiés. Pour interroger le contenu du fichier à l’aide d’une requête LINQ, l’application pourrait charger le contenu du fichier dans un tableau ou une collection. Toutefois, le chargement de l’intégralité du fichier dans un tableau ou une collection consommerait beaucoup plus de mémoire que nécessaire. La requête LINQ pourrait à la place interroger le contenu du fichier en utilisant une classe énumérable, en retournant uniquement les valeurs qui correspondent aux critères de recherche. Les requêtes qui retournent uniquement quelques valeurs correspondantes consomme beaucoup moins de mémoire.  
  
 Vous pouvez créer une classe qui implémente le <xref:System.Collections.Generic.IEnumerable%601>interface à exposer des données sources comme données énumérables.</xref:System.Collections.Generic.IEnumerable%601> Votre classe qui implémente le `IEnumerable(T)` interface demandera une autre classe qui implémente le <xref:System.Collections.Generic.IEnumerator%601>interface pour itérer la source de données.</xref:System.Collections.Generic.IEnumerator%601> Ces deux classes permettent de retourner séquentiellement comme un type spécifique des éléments de données.  
  
 Dans cette procédure pas à pas, vous allez créer une classe qui implémente le `IEnumerable(Of String)` interface et une classe qui implémente le `IEnumerator(Of String)` interface pour lire une fichier texte une ligne à la fois.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Création de la classe Enumerable  
  
|Pour créer le projet de classe enumerable|  
|---|  
|1.  Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.<br />2.  Dans le **nouveau projet** boîte de dialogue le **Types de projet** volet, assurez-vous que **Windows** est sélectionnée. Sélectionnez **bibliothèque de classes** dans les **modèles** volet. Dans le **nom** , tapez `StreamReaderEnumerable`, puis cliquez sur **OK**. Le nouveau projet s’affiche.<br />3.  Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**. Renommez le fichier `StreamReaderEnumerable.vb` et appuyez sur ENTRÉE. Renommer le fichier sera également renommer la classe `StreamReaderEnumerable`. Cette classe implémente le `IEnumerable(Of String)` interface.<br />4.  Cliquez sur le projet StreamReaderEnumerable, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Sélectionnez le **classe** modèle. Dans le **nom** , tapez `StreamReaderEnumerator.vb` sur **OK**.|  
  
 La première classe dans ce projet est la classe enumerable et implémentez la `IEnumerable(Of String)` interface. Cette interface générique implémente le <xref:System.Collections.IEnumerable>interface et garantit que les consommateurs de cette classe peuvent accéder aux valeurs de type `String`.</xref:System.Collections.IEnumerable>  
  
|Pour ajouter le code pour implémenter IEnumerable|  
|---|  
|1.  Ouvrez le fichier StreamReaderEnumerable.vb.<br />2.  Sur la ligne après `Public Class StreamReaderEnumerable`, tapez la commande suivante et appuyez sur ENTRÉE.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&1;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]remplit automatiquement la classe avec les membres qui sont requis par le `IEnumerable(Of String)` interface.<br />3.  Cette classe énumérable lira les lignes à partir d’une fichier texte une ligne à la fois. Ajoutez le code suivant à la classe pour exposer un constructeur public qui accepte un chemin d’accès de fichier comme paramètre d’entrée.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&2;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Votre implémentation de la <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>méthode de la `IEnumerable(Of String)` interface retourne une nouvelle instance de la `StreamReaderEnumerator` classe</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> L’implémentation de la `GetEnumerator` procédé de la `IEnumerable` interface peut être effectuée `Private`, car vous devez n'exposer que les membres de le `IEnumerable(Of String)` interface. Remplacez le code qui [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] généré pour le `GetEnumerator` méthodes avec le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&3;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Pour ajouter le code pour implémenter IEnumerator|  
|---|  
|1.  Ouvrez le fichier StreamReaderEnumerator.vb.<br />2.  Sur la ligne après `Public Class StreamReaderEnumerator`, tapez la commande suivante et appuyez sur ENTRÉE.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&4;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]remplit automatiquement la classe avec les membres qui sont requis par le `IEnumerator(Of String)` interface.<br />3.  La classe d’énumérateur ouvre le fichier texte et exécute le fichier d’e/s pour lire les lignes à partir du fichier. Ajoutez le code suivant à la classe pour exposer un constructeur public qui accepte un chemin d’accès de fichier comme paramètre d’entrée et ouvrez le fichier texte pour la lecture.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&5;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  Le `Current` propriétés à la fois pour le `IEnumerator(Of String)` et `IEnumerator` interfaces retournent l’élément actuel du fichier texte comme un `String`. L’implémentation de la `Current` propriété de la `IEnumerator` interface peut être effectuée `Private`, car vous devez n'exposer que les membres de le `IEnumerator(Of String)` interface. Remplacez le code qui [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] généré pour les `Current` propriétés par le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&6;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  Le `MoveNext` procédé de la `IEnumerator` interface navigue jusqu'à l’élément suivant dans le fichier texte et met à jour la valeur retournée par le `Current` propriété. Si aucun élément à lire, plus le `MoveNext` méthode renvoie `False`; sinon la `MoveNext` méthode renvoie `True`. Ajoutez le code suivant à la méthode `MoveNext`.<br />     [!code-vb[VbVbalrIteratorWalkthrough&#7;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  Le `Reset` procédé de la `IEnumerator` interface ordonne à l’itérateur pour pointer vers le début du fichier texte et efface la valeur de l’élément actuel. Ajoutez le code suivant à la méthode `Reset`.<br />     [!code-vb[VbVbalrIteratorWalkthrough n °&8;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  Le `Dispose` procédé de la `IEnumerator` interface garantit que toutes les ressources non managées sont libérées avant la destruction de l’itérateur. Le handle de fichier est utilisé par le `StreamReader` objet est une ressource non managée et doit être fermé avant la destruction de l’instance de l’itérateur. Remplacez le code qui [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] généré pour le `Dispose` méthode par le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough&#9;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>À l’aide de l’itérateur d’exemple  
 Vous pouvez utiliser une classe énumérable dans votre code avec les structures de contrôle qui ont besoin d’un objet qui implémente `IEnumerable`, comme un `For Next` boucle ou une requête LINQ. L’exemple suivant illustre le `StreamReaderEnumerable` dans une requête LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough&#10;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next (instruction)](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)

