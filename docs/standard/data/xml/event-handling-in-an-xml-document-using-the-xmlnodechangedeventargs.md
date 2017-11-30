---
title: "Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2bfd6eee5831b6bb92c0274fe5925184c80a92e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="0322c-102">Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="0322c-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="0322c-103">Le **XmlNodeChangedEventArgs** encapsule les arguments passés aux gestionnaires d’événements inscrits sur le **XmlDocument** objet pour la gestion des événements.</span><span class="sxs-lookup"><span data-stu-id="0322c-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="0322c-104">Le tableau suivant répertorie ces événements et fournit une description des circonstances dans lesquelles ils sont déclenchés :</span><span class="sxs-lookup"><span data-stu-id="0322c-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="0322c-105">Événement</span><span class="sxs-lookup"><span data-stu-id="0322c-105">Event</span></span>|<span data-ttu-id="0322c-106">Est déclenché</span><span class="sxs-lookup"><span data-stu-id="0322c-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="0322c-107">Quand un nœud faisant partie du document actif est sur le point d'être inséré dans un autre nœud.</span><span class="sxs-lookup"><span data-stu-id="0322c-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="0322c-108">Quand un nœud faisant partie du document actif a été inséré dans un autre nœud.</span><span class="sxs-lookup"><span data-stu-id="0322c-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="0322c-109">Quand un nœud faisant partie du document en cours est sur le point d'être supprimé du document.</span><span class="sxs-lookup"><span data-stu-id="0322c-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="0322c-110">Quand un nœud faisant partie de ce document a été supprimé de son parent.</span><span class="sxs-lookup"><span data-stu-id="0322c-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="0322c-111">Quand la valeur d'un nœud est sur le point d'être modifiée.</span><span class="sxs-lookup"><span data-stu-id="0322c-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="0322c-112">Quand la valeur d'un nœud a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="0322c-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0322c-113">Si le **XmlDataDocument** utilisation de la mémoire est entièrement optimisée pour utiliser **DataSet** stockage, le **XmlDataDocument** peuvent ne pas déclencher les événements répertoriés ci-dessus lorsque des modifications sont sous-jacentes **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="0322c-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="0322c-114">Si vous avez besoin de ces événements, vous devez traverser l’intégralité **XmlDocument** une fois pour rendre l’utilisation de la mémoire non entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="0322c-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="0322c-115">L'exemple de code suivant illustre la définition d'un gestionnaire d'événements et l'ajout de celui-ci à un événement :</span><span class="sxs-lookup"><span data-stu-id="0322c-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="0322c-116">Certaines opérations Document Object Model (DOM) XML sont des opérations composées pouvant entraîner le déclenchement de plusieurs événements.</span><span class="sxs-lookup"><span data-stu-id="0322c-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="0322c-117">Par exemple, **AppendChild** peut-être également supprimer le nœud ajouté de son parent précédent.</span><span class="sxs-lookup"><span data-stu-id="0322c-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="0322c-118">Dans ce cas, vous voyez un **NodeRemoved** l’événement déclenché en premier, suivi d’un **NodeInserted** événement.</span><span class="sxs-lookup"><span data-stu-id="0322c-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="0322c-119">Les opérations telles que la définition **InnerXml** peuvent provoquer plusieurs événements.</span><span class="sxs-lookup"><span data-stu-id="0322c-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="0322c-120">L’exemple de code suivant illustre la création du Gestionnaire d’événements et la gestion de la **NodeInserted** événement.</span><span class="sxs-lookup"><span data-stu-id="0322c-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 <span data-ttu-id="0322c-121">Pour plus d’informations, consultez <xref:System.Xml.XmlNodeChangedEventArgs> et <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0322c-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0322c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0322c-122">See Also</span></span>  
 [<span data-ttu-id="0322c-123">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="0322c-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
