---
title: "Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ab75113ca2609385db8be9d79563e7b71dfd0b5b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="3b086-102">Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b086-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="3b086-103">Cet exemple montre comment fusionner des données provenant de sources différentes en une séquence de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="3b086-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b086-104">N’essayez pas de joindre des données ou des données en mémoire dans le système de fichiers avec des données qui se trouve toujours dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="3b086-104">Do not try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="3b086-105">Ces jointures interdomaines peuvent générer des résultats indéfinis en raison de différentes façons dans lequel les opérations de jointure peuvent être définies pour les requêtes de base de données et d’autres types de sources.</span><span class="sxs-lookup"><span data-stu-id="3b086-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="3b086-106">En outre, il est un risque qu’une telle opération pourrait provoquer une exception de mémoire insuffisante si la quantité de données dans la base de données est suffisante.</span><span class="sxs-lookup"><span data-stu-id="3b086-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="3b086-107">Pour joindre des données d’une base de données en mémoire, appelez d’abord `ToList` ou `ToArray` sur la base de données de requête, puis effectuez la jointure sur la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="3b086-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="3b086-108">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="3b086-108">To create the data file</span></span>  
  
-   <span data-ttu-id="3b086-109">Copiez les fichiers names.csv et scores.csv dans votre dossier de projet, comme décrit dans [Comment : joindre contenu à partir de différents fichiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="3b086-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b086-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b086-110">Example</span></span>  
 <span data-ttu-id="3b086-111">L’exemple suivant montre comment utiliser un type nommé `Student` pour stocker les données fusionnées à partir de deux collections en mémoire de chaînes qui simulent des données de feuille de calcul au format .csv.</span><span class="sxs-lookup"><span data-stu-id="3b086-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="3b086-112">La première collection de chaînes représente les noms des étudiants et les ID et la deuxième collection représente l’ID de l’étudiant (dans la première colonne) et quatre notes d’examen.</span><span class="sxs-lookup"><span data-stu-id="3b086-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="3b086-113">L’ID est utilisé comme clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="3b086-113">The ID is used as the foreign key.</span></span>  
  
```vb  
Class Student  
    Public FirstName As String  
    Public LastName As String  
    Public ID As Integer  
    Public ExamScores As List(Of Integer)  
End Class  
  
Class PopulateCollection  
  
    Shared Sub Main()  
  
        ' Merge content from spreadsheets into a list of Student objects.  
  
        ' These data files are defined in How to: Join Content from   
        ' Dissimilar Files (LINQ).  
  
        ' Each line of names.csv consists of a last name, a first name, and an  
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
  
        ' Each line of scores.csv consists of an ID number and four test   
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' The following query merges the content of two dissimilar spreadsheets   
        ' based on common ID values.  
        ' Multiple From clauses are used instead of a Join clause  
        ' in order to store the results of scoreLine.Split.  
        ' Note the dynamic creation of a list of integers for the  
        ' ExamScores member. We skip the first item in the split string   
        ' because it is the student ID, not an exam score.  
        Dim queryNamesScores = From nameLine In names  
                          Let splitName = nameLine.Split(New Char() {","})  
                          From scoreLine In scores  
                          Let splitScoreLine = scoreLine.Split(New Char() {","})  
                          Where splitName(2) = splitScoreLine(0)  
                          Select New Student() With {  
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),  
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                                             Select Convert.ToInt32(scoreAsText)).ToList()}  
  
        ' Optional. Store the query results for faster access in future  
        ' queries. This could be useful with very large data files.  
        Dim students As List(Of Student) = queryNamesScores.ToList()  
  
        ' Display each student's name and exam score average.  
        For Each s In students  
            Console.WriteLine("The average score of " & s.FirstName & " " &  
                              s.LastName & " is " & s.ExamScores.Average())  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
  
' Output:   
' The average score of Omelchenko Svetlana is 82.5  
' The average score of O'Donnell Claire is 72.25  
' The average score of Mortensen Sven is 84.5  
' The average score of Garcia Cesar is 88.25  
' The average score of Garcia Debra is 67  
' The average score of Fakhouri Fadi is 92.25  
' The average score of Feng Hanying is 88  
' The average score of Garcia Hugo is 85.75  
' The average score of Tucker Lance is 81.75  
' The average score of Adams Terry is 85.25  
' The average score of Zabokritski Eugene is 83  
' The average score of Tucker Michael is 92  
```  
  
 <span data-ttu-id="3b086-114">Dans le [Clause Select](../../../../visual-basic/language-reference/queries/select-clause.md) clause, un initialiseur d’objet est utilisé pour instancier chaque nouvel `Student` objet en utilisant les données des deux sources.</span><span class="sxs-lookup"><span data-stu-id="3b086-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>  
  
 <span data-ttu-id="3b086-115">Si vous n’êtes pas obligé de stocker les résultats d’une requête, les types anonymes peuvent être plus pratiques que les types nommés.</span><span class="sxs-lookup"><span data-stu-id="3b086-115">If you do not have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="3b086-116">Types nommés sont requis si vous passez les résultats de requête en dehors de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="3b086-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="3b086-117">L’exemple suivant effectue la même tâche que l’exemple précédent, mais utilise des types anonymes au lieu de types nommés :</span><span class="sxs-lookup"><span data-stu-id="3b086-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>  
  
```vb  
' Merge the data by using an anonymous type.   
' Note the dynamic creation of a list of integers for the  
' ExamScores member. We skip 1 because the first string  
' in the array is the student ID, not an exam score.  
Dim queryNamesScores2 =  
    From nameLine In names  
    Let splitName = nameLine.Split(New Char() {","})  
    From scoreLine In scores  
    Let splitScoreLine = scoreLine.Split(New Char() {","})  
    Where splitName(2) = splitScoreLine(0)  
    Select New With  
           {.Last = splitName(0),  
            .First = splitName(1),  
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                           Select Convert.ToInt32(scoreAsText)).ToList()}  
  
' Display each student's name and exam score average.  
For Each s In queryNamesScores2  
    Console.WriteLine("The average score of " & s.First & " " &  
                      s.Last & " is " & s.ExamScores.Average())  
Next  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b086-118">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3b086-118">Compiling the Code</span></span>  
 <span data-ttu-id="3b086-119">Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="3b086-119">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b086-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b086-120">See Also</span></span>  
 [<span data-ttu-id="3b086-121">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b086-121">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
