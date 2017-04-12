---
title: "Création du Document Office Open XML Source (Visual Basic) | Documents Microsoft"
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
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 928a3c34836464e7603c485b64c9c426913ae7b2
ms.lasthandoff: 03/13/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Création du Document Office Open XML Source (Visual Basic)
Cette rubrique montre comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel. Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.  
  
 Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.  
  
 Pour créer le document utilisé par ce didacticiel, vous devez avoir Microsoft Office 2007 ou version ultérieure, ou vous devez disposer de Microsoft Office 2003 avec le Pack de compatibilité Microsoft Office pour Word, Excel et Formats de fichier PowerPoint 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Création du document WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Pour créer le document WordprocessingML  
  
1.  Créez un nouveau document Microsoft Word.  
  
2.  Collez le texte suivant dans le nouveau document :  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  Mettez en forme la première ligne à l'aide du style « Titre 1 ».  
  
4.  Sélectionnez les lignes qui contiennent le code Visual Basic. La première ligne commence par le mot clé `Imports`. La dernière ligne est « End Class ». Mettez en forme les lignes avec la police Courrier. Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».  
  
5.  Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.  
  
6.  Enregistrez le document et nommez-le SampleDoc.docx.  
  
    > [!NOTE]
    >  Si vous utilisez Microsoft Word 2003, sélectionnez **Document Word 2007** dans les **enregistrer en tant que Type** liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
