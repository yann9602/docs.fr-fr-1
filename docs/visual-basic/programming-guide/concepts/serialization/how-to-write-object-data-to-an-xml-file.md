---
title: "Comment : écrire des données d’objet dans un fichier XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 146ccb7b1999049106d5f0be1ce78e740dfcf060
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Comment : écrire des données d’objet dans un fichier XML (Visual Basic)
Exemple de cet exemple écrit l’objet d’une classe dans un fichier XML à l’aide de la <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="example"></a>Exemple  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 La classe doit avoir un constructeur public sans paramètres.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   La classe en cours de sérialisation ne dispose pas d’un constructeur sans paramètre public.  
  
-   Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
-   Le chemin d’accès est trop long (<xref:System.IO.PathTooLongException>).</xref:System.IO.PathTooLongException>  
  
-   Le disque est saturé (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Cet exemple crée un nouveau fichier, si le fichier n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de `Create` accès pour le dossier. Si le fichier existe déjà, l’application doit uniquement `Write` accéder, un privilège inférieur. Si possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder `Read` accès à un seul fichier, plutôt que `Create` accès pour un dossier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [Comment : lire des données d’objet à partir d’un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [Sérialisation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
