---
title: "Comment : lire des données d’objet à partir d’un fichier XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c448d79a88517925712f79ed061aa90933e3f6d1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Comment : lire des données d’objet à partir d’un fichier XML (Visual Basic)
Cet exemple lit les données d’objet écrites précédemment dans un fichier XML à l’aide de la <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="example"></a>Exemple  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier contenant les données sérialisées. Pour plus d’informations sur la sérialisation des données, consultez la page [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 La classe doit avoir un constructeur public sans paramètres.  
  
 Seuls les champs et propriétés publics sont désérialisés.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   La classe en cours de sérialisation ne dispose pas d’un constructeur sans paramètre public.  
  
-   Les données dans le fichier ne représentent pas les données à partir de la classe à désérialiser.  
  
-   Le fichier n’existe pas (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Vérifiez toujours les entrées et jamais désérialiser des données à partir d’une source non fiable. L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [Sérialisation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)
