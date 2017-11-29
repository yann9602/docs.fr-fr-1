---
title: Guide pratique pour lire des fichiers texte avec plusieurs formats en Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12362f932561bf16412e5beb364f785778c58814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Guide pratique pour lire des fichiers texte avec plusieurs formats en Visual Basic
L’objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux. Vous pouvez traiter un fichier contenant plusieurs formats en utilisant la méthode `PeekChars` pour déterminer le format de chaque ligne à mesure que vous analysez le fichier.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Pour analyser un fichier texte avec plusieurs formats  
  
1.  Ajoutez un fichier texte nommé testfile.txt à votre projet. Ajoutez le contenu suivant au fichier texte.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Définissez le format attendu et le format utilisé quand une erreur est signalée. La dernière entrée dans chaque tableau étant -1, le dernier champ est supposé avoir une largeur variable. Cela se produit quand la dernière entrée du tableau est inférieure ou égale à 0.  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  Créez un nouvel objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> en définissant la largeur et le format.  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  Parcourez les lignes en boucle, en testant le format avant la lecture.  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  Écrivez les erreurs dans la console.  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a>Exemple  
 Voici l’exemple complet qui lit le fichier `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.  
  
-   Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.Security.SecurityException>).  
  
-   Le chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
-   L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [Guide pratique : lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Guide pratique : lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Analyse des fichiers texte avec l’objet TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
