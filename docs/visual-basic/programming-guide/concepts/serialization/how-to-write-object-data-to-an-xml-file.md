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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 27131f357c1f5afc75645bff88ae5d7cd2395617
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="02ab7-102">Comment : écrire des données d’objet dans un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ab7-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="02ab7-103">Exemple de cet exemple écrit l’objet d’une classe dans un fichier XML à l’aide de la <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="02ab7-103">TThis example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ab7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="02ab7-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="02ab7-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="02ab7-105">Compiling the Code</span></span>  
 <span data-ttu-id="02ab7-106">La classe doit avoir un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="02ab7-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="02ab7-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="02ab7-107">Robust Programming</span></span>  
 <span data-ttu-id="02ab7-108">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="02ab7-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="02ab7-109">La classe en cours de sérialisation ne dispose pas d’un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="02ab7-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="02ab7-110">Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="02ab7-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="02ab7-111">Le chemin d’accès est trop long (<xref:System.IO.PathTooLongException>).</xref:System.IO.PathTooLongException></span><span class="sxs-lookup"><span data-stu-id="02ab7-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="02ab7-112">Le disque est saturé (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="02ab7-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="02ab7-113">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02ab7-113">.NET Framework Security</span></span>  
 <span data-ttu-id="02ab7-114">Cet exemple crée un nouveau fichier, si le fichier n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="02ab7-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="02ab7-115">Si une application doit créer un fichier, elle doit disposer de `Create` accès pour le dossier.</span><span class="sxs-lookup"><span data-stu-id="02ab7-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="02ab7-116">Si le fichier existe déjà, l’application doit uniquement `Write` accéder, un privilège inférieur.</span><span class="sxs-lookup"><span data-stu-id="02ab7-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="02ab7-117">Si possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder `Read` accès à un seul fichier, plutôt que `Create` accès pour un dossier.</span><span class="sxs-lookup"><span data-stu-id="02ab7-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ab7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ab7-118">See Also</span></span>  
 <span data-ttu-id="02ab7-119"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="02ab7-119"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="02ab7-120"> [Comment : lire des données d’objet à partir d’un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="02ab7-120"> [How to: Read Object Data from an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span></span>  
<span data-ttu-id="02ab7-121"> [Sérialisation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span><span class="sxs-lookup"><span data-stu-id="02ab7-121"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span></span>
