---
title: "Walkthrough: Implementing IEnumerable(Of T) in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "control flow [Visual Basic]"
  - "enumerable interfaces"
  - "loop structures, optimizing performance"
  - "control flow"
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Walkthrough: Implementing IEnumerable(Of T) in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'interface <xref:System.Collections.Generic.IEnumerable%601> est implémentée par les classes qui peuvent retourner une séquence de valeurs élément par élément.  L'avantage du retour de données élément par élément est que vous n'avez pas à charger le groupe de données complet dans la mémoire pour l'utiliser.  Vous devez simplement utiliser la mémoire nécessaire au chargement d'un seul élément à partir des données.  Les classes qui implémentent l'interface `IEnumerable(T)` peuvent être utilisées avec les boucles `For Each` ou les requêtes LINQ.  
  
 Par exemple, prenez une application qui doit lire un fichier texte volumineux et retourner chaque ligne du fichier correspondant aux critères de recherche particuliers.  L'application utilise une requête LINQ pour retourner les lignes du fichier qui correspondent aux critères spécifiés.  Pour interroger le contenu du fichier à l'aide d'une requête LINQ, l'application pourrait charger le contenu du fichier dans un tableau ou une collection.  Toutefois, le chargement du fichier tout entier dans un tableau ou une collection consommerait beaucoup plus de mémoire que nécessaire.  La requête LINQ pourrait à la place interroger le contenu du fichier à l'aide d'une classe énumérable, en retournant uniquement les valeurs correspondant aux critères de recherche.  Les requêtes qui retournent uniquement quelques valeurs correspondantes consommeraient beaucoup moins de mémoire.  
  
 Vous pouvez créer une classe qui implémente l'interface <xref:System.Collections.Generic.IEnumerable%601> pour exposer des données sources comme données énumérables.  Votre classe qui implémente l'interface `IEnumerable(T)` demandera une autre classe implémentant l'interface <xref:System.Collections.Generic.IEnumerator%601> pour effectuer une itération au sein des données sources.  Ces deux classes vous permettent de retourner séquentiellement des éléments de données comme type spécifique.  
  
 Dans cette procédure pas à pas, vous allez créer une classe qui implémente l'interface `IEnumerable(Of String)` et une classe qui implémente l'interface `IEnumerator(Of String)` pour lire un fichier texte ligne par ligne.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## Création de la classe énumérable  
  
||  
|-|  
|Pour créer le projet de classe énumérable|  
|1.  Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.<br />2.  Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.  Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**.  Dans la zone **Nom**, tapez `StreamReaderEnumerable`, puis cliquez sur **OK**.  Le nouveau projet s'affiche.<br />3.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier Class1.vb, puis cliquez sur **Renommer**.  Renommez le fichier en `StreamReaderEnumerable.vb` et appuyez sur ENTRÉE.  Lorsque vous renommez le fichier, la classe sera également renommée en `StreamReaderEnumerable`.  Cette classe implémentera l'interface `IEnumerable(Of String)`.<br />4.  Cliquez avec le bouton droit sur le projet StreamReaderEnumerable, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  Sélectionnez le modèle **Classe**.  Dans la zone **Nom**, tapez `StreamReaderEnumerator.vb` et cliquez sur **OK**.|  
  
 La première classe dans ce projet est la classe énumérable qui implémentera l'interface `IEnumerable(Of String)`.  Cette interface générique implémente l'interface <xref:System.Collections.IEnumerable> et garantit que les consommateurs de cette classe peuvent accéder aux valeurs de type `String`.  
  
||  
|-|  
|Pour ajouter le code pour implémenter IEnumerable|  
|1.  Ouvrez le fichier StreamReaderEnumerable.vb.<br />2.  Sur la ligne suivant `Public Class StreamReaderEnumerable`, tapez ce qui suit et appuyez sur ENTRÉE.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#1)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] remplit automatiquement la classe avec les membres requis par l'interface `IEnumerable(Of String)`<br />3.  Cette classe énumérable lira les lignes d'un fichier texte une par une.  Ajoutez le code suivant à la classe pour exposer un constructeur public prenant un chemin d'accès de fichier comme paramètre d'entrée.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#2)]<br />4.  Votre implémentation de la méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> de l'interface `IEnumerable(Of String)` retournera une nouvelle instance de la classe `StreamReaderEnumerator`.  L'implémentation de la méthode `GetEnumerator` de l'interface `IEnumerable` peut devenir `Private` car vous ne devez exposer que les membres de l'interface `IEnumerable(Of String)`.  Remplacez le code généré par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour les méthodes `GetEnumerator` par le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#3)]|  
  
||  
|-|  
|Pour ajouter le code pour implémenter IEnumerator|  
|1.  Ouvrez le fichier StreamReaderEnumerator.vb.<br />2.  Sur la ligne suivant `Public Class StreamReaderEnumerator`, tapez ce qui suit et appuyez sur ENTRÉE.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#4)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] remplit automatiquement la classe avec les membres requis par l'interface `IEnumerator(Of String)`<br />3.  La classe d'énumérateur ouvre le fichier texte et exécute l'E\/S de fichier pour lire les lignes du fichier.  Ajoutez le code suivant à la classe pour exposer un constructeur public prenant un chemin d'accès de fichier comme paramètre d'entrée et ouvrez le fichier texte pour la lecture.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#5)]<br />4.  Les propriétés `Current` pour les interfaces `IEnumerator(Of String)` et `IEnumerator` retournent l'élément actuel du fichier texte comme `String`.  L'implémentation de la propriété `Current` de l'interface `IEnumerator` peut devenir `Private` car vous ne devez exposer que les membres de l'interface `IEnumerator(Of String)`.  Remplacez le code généré par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour les propriétés `Current` par le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#6)]<br />5.  La méthode `MoveNext` de l'interface `IEnumerator` navigue jusqu'à l'élément suivant du fichier texte et met à jour la valeur retournée par la propriété `Current`.  Si le fichier ne contient aucun élément à lire, la méthode `MoveNext` retourne la valeur `False` ; sinon, la méthode `MoveNext` retourne la valeur `True`.  Ajoutez le code suivant à la méthode `MoveNext`.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#7)]<br />6.  La méthode `Reset` de l'interface `IEnumerator` ordonne à l'itérateur de pointer sur le début du fichier texte et efface la valeur d'élément actuelle.  Ajoutez le code suivant à la méthode `Reset`.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#8)]<br />7.  La méthode `Dispose` de l'interface `IEnumerator` garantit que toutes les ressources non managées sont libérées avant la destruction de l'itérateur.  Le descripteur de fichier utilisé par l'objet `StreamReader` est une ressource non managée et doit être fermé avant la destruction de l'instance de l'itérateur.  Remplacez le code généré par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour la méthode `Dispose` par le code suivant.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/StreamReaderIterator.vb#9)]|  
  
## Utilisation de l'itérateur d'exemple  
 Vous pouvez utiliser une classe énumérable dans votre code avec les structures de contrôle qui requièrent un objet implémentant `IEnumerable`, tel qu'une boucle `For Next` ou une requête LINQ.  L'exemple suivant illustre `StreamReaderEnumerable` dans une requête LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/visualbasic/VbVbalrIteratorWalkthrough/Module1.vb#10)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)