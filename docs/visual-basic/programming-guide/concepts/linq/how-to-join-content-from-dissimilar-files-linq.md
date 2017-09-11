---
title: "Comment : joindre du contenu issu de différents fichiers (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: e7530857-c467-41ea-9730-84e6b1065a4d
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
ms.openlocfilehash: 728c2b268b9ce6185f1c4ef8bd28915f1bafc8c5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-join-content-from-dissimilar-files-linq-visual-basic"></a><span data-ttu-id="92a1d-102">Comment : joindre du contenu issu de différents fichiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92a1d-102">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="92a1d-103">Cet exemple montre comment joindre des données de deux fichiers CSV qui partagent une valeur commune utilisée comme clé correspondante.</span><span class="sxs-lookup"><span data-stu-id="92a1d-103">This example shows how to join data from two comma-delimited files that share a common value that is used as a matching key.</span></span> <span data-ttu-id="92a1d-104">Cette technique peut être utile si vous devez combiner les données de deux feuilles de calcul ou une feuille de calcul et d’un fichier qui a un autre format, dans un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="92a1d-104">This technique can be useful if you have to combine data from two spreadsheets, or from a spreadsheet and from a file that has another format, into a new file.</span></span> <span data-ttu-id="92a1d-105">Vous pouvez modifier l’exemple pour utiliser tout type de texte structuré.</span><span class="sxs-lookup"><span data-stu-id="92a1d-105">You can modify the example to work with any kind of structured text.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="92a1d-106">Pour créer les fichiers de données</span><span class="sxs-lookup"><span data-stu-id="92a1d-106">To create the data files</span></span>  
  
1.  <span data-ttu-id="92a1d-107">Copiez les lignes suivantes dans un fichier nommé scores.csv et enregistrez-le dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="92a1d-107">Copy the following lines into a file that is named scores.csv and save it to your project folder.</span></span> <span data-ttu-id="92a1d-108">Le fichier représente les données de feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="92a1d-108">The file represents spreadsheet data.</span></span> <span data-ttu-id="92a1d-109">La colonne 1 est l’ID de l’étudiant et les colonnes 2 à 5 des résultats de test.</span><span class="sxs-lookup"><span data-stu-id="92a1d-109">Column 1 is the student's ID, and columns 2 through 5 are test scores.</span></span>  
  
    ```  
    111, 97, 92, 81, 60  
    112, 75, 84, 91, 39  
    113, 88, 94, 65, 91  
    114, 97, 89, 85, 82  
    115, 35, 72, 91, 70  
    116, 99, 86, 90, 94  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    119, 68, 79, 88, 92  
    120, 99, 82, 81, 79  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    ```  
  
2.  <span data-ttu-id="92a1d-110">Copiez les lignes suivantes dans un fichier nommé names.csv et enregistrez-le dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="92a1d-110">Copy the following lines into a file that is named names.csv and save it to your project folder.</span></span> <span data-ttu-id="92a1d-111">Le fichier représente une feuille de calcul qui contient le nom de l’étudiant, prénom et ID étudiant.</span><span class="sxs-lookup"><span data-stu-id="92a1d-111">The file represents a spreadsheet that contains the student's last name, first name, and student ID.</span></span>  
  
    ```  
    Omelchenko,Svetlana,111  
    O'Donnell,Claire,112  
    Mortensen,Sven,113  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Hugo,118  
    Tucker,Lance,119  
    Adams,Terry,120  
    Zabokritski,Eugene,121  
    Tucker,Michael,122  
    ```  
  
## <a name="example"></a><span data-ttu-id="92a1d-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="92a1d-112">Example</span></span>  
  
```vb  
Class JoinStrings  
  
    Shared Sub Main()  
  
        ' Join content from spreadsheet files that contain  
        ' related information. names.csv contains the student name  
        ' plus an ID number. scores.csv contains the ID and a   
        ' set of four test scores. The following query joins  
        ' the scores to the student names by using ID as a  
        ' matching key.  
  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Name:    Last[0],       First[1],  ID[2],     Grade Level[3]  
        '          Omelchenko,    Svetlana,  111,       2  
        ' Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]  
        '          111,           97,        92,        81,        60  
  
        ' This query joins two dissimilar spreadsheets based on common ID value.  
        ' Multiple from clauses are used instead of a join clause  
        ' in order to store results of id.Split.  
        Dim scoreQuery1 = From name In names   
                         Let n = name.Split(New Char() {","})   
                            From id In scores   
                            Let n2 = id.Split(New Char() {","})   
                            Where n(2) = n2(0)   
                            Select n(0) & "," & n(1) & "," & n2(0) & "," & n2(1) & "," &  
                              n2(2) & "," & n2(3)  
  
        ' Pass a query variable to a Sub and execute it there.  
        ' The query itself is unchanged.  
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)  
  
        Console.WriteLine(System.Environment.NewLine & message)  
        For Each item As String In query  
            Console.WriteLine(item)  
        Next  
        Console.WriteLine(query.Count & " total names in list")  
  
    End Sub  
End Class  
' Output:  
'Merge two spreadsheets:  
'Adams,Terry,120, 99, 82, 81  
'Fakhouri,Fadi,116, 99, 86, 90  
'Feng,Hanying,117, 93, 92, 80  
'Garcia,Cesar,114, 97, 89, 85  
'Garcia,Debra,115, 35, 72, 91  
'Garcia,Hugo,118, 92, 90, 83  
'Mortensen,Sven,113, 88, 94, 65  
'O'Donnell,Claire,112, 75, 84, 91  
'Omelchenko,Svetlana,111, 97, 92, 81  
'Tucker,Lance,119, 68, 79, 88  
'Tucker,Michael,122, 94, 92, 91  
'Zabokritski,Eugene,121, 96, 85, 91  
'12 total names in list  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92a1d-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="92a1d-113">Compiling the Code</span></span>  
 <span data-ttu-id="92a1d-114">Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="92a1d-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a1d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92a1d-115">See Also</span></span>  
 <span data-ttu-id="92a1d-116">[LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="92a1d-116">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="92a1d-117"> [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="92a1d-117"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
