---
title: "Guide pratique pour lire des fichiers texte délimités par des virgules en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd88762179d9760bcce37b4c500a2bb118e09173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Guide pratique pour lire des fichiers texte délimités par des virgules en Visual Basic
L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux. La propriété `TextFieldType` définit s’il s’agit d’un fichier délimité ou d’un fichier avec des champs de texte de longueur fixe.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Pour analyser un fichier texte délimité par des virgules  
  
1.  Créez un `TextFieldParser`. Le code suivant crée le `TextFieldParser` nommé `MyReader` et ouvre le fichier `test.txt`.  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  Définissez le type `TextField` et le séparateur. Le code suivant définit la propriété `TextFieldType` comme `Delimited` et le délimiteur comme ",".  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  Parcourez les champs du fichier à l’aide d’une boucle. Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse. Le code suivant parcourt le fichier à l’aide d’une boucle, affiche chaque champ l’un après l’autre et signale les champs dont le format n’est pas valide.  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  Fermez les blocs `While` et `Using` avec `End While` et `End Using`.  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple lit le fichier `test.txt`.  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.  
  
-   Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.Security.SecurityException>).  
  
-   Le chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
-   L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [Guide pratique : lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Guide pratique : lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Analyse des fichiers texte avec l’objet TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Dépannage : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
