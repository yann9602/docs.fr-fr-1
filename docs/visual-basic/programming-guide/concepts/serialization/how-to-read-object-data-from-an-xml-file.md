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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3b9697f763a2d781c37960d46cbc7fa4536c84b4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="ad46b-102">Comment : lire des données d’objet à partir d’un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad46b-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="ad46b-103">Cet exemple lit les données d’objet écrites précédemment dans un fichier XML à l’aide de la <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="ad46b-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad46b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad46b-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad46b-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ad46b-105">Compiling the Code</span></span>  
 <span data-ttu-id="ad46b-106">Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier contenant les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="ad46b-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="ad46b-107">Pour plus d’informations sur la sérialisation des données, consultez la page [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="ad46b-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="ad46b-108">La classe doit avoir un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="ad46b-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="ad46b-109">Seuls les champs et propriétés publics sont désérialisés.</span><span class="sxs-lookup"><span data-stu-id="ad46b-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ad46b-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ad46b-110">Robust Programming</span></span>  
 <span data-ttu-id="ad46b-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="ad46b-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ad46b-112">La classe en cours de sérialisation ne dispose pas d’un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="ad46b-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="ad46b-113">Les données dans le fichier ne représentent pas les données à partir de la classe à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="ad46b-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="ad46b-114">Le fichier n’existe pas (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="ad46b-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ad46b-115">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad46b-115">.NET Framework Security</span></span>  
 <span data-ttu-id="ad46b-116">Vérifiez toujours les entrées et jamais désérialiser des données à partir d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="ad46b-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="ad46b-117">L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé.</span><span class="sxs-lookup"><span data-stu-id="ad46b-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="ad46b-118">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="ad46b-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad46b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad46b-119">See Also</span></span>  
 <span data-ttu-id="ad46b-120"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="ad46b-120"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="ad46b-121"> [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="ad46b-121"> [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span></span>  
<span data-ttu-id="ad46b-122"> [Sérialisation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad46b-122"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span></span>  
<span data-ttu-id="ad46b-123"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="ad46b-123"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md)</span></span>
