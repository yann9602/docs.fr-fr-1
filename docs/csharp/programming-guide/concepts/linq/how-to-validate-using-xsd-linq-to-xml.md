---
title: "Guide pratique pour valider à l’aide de XSD (LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cec3090541f7bbc306eb41fff409dc890cc55d17
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="842a4-102">Guide pratique pour valider à l’aide de XSD (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="842a4-102">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="842a4-103">L'espace de noms <xref:System.Xml.Schema> contient des méthodes d'extension qui facilitent la validation d'une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="842a4-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="842a4-104">Pour plus d'informations, consultez la documentation sur la méthode <xref:System.Xml.Schema.Extensions.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="842a4-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="842a4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="842a4-105">Example</span></span>  
 <span data-ttu-id="842a4-106">L'exemple suivant crée un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis valide deux objets <xref:System.Xml.Linq.XDocument> par rapport au jeu de schémas.</span><span class="sxs-lookup"><span data-stu-id="842a4-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="842a4-107">L'un des documents est valide, l'autre non.</span><span class="sxs-lookup"><span data-stu-id="842a4-107">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="842a4-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="842a4-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="842a4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="842a4-109">Example</span></span>  
 <span data-ttu-id="842a4-110">L’exemple suivant confirme que le document XML de l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) est valide par rapport au schéma de l’[Exemple de fichier XSD : Clients et commandes](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="842a4-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="842a4-111">Il modifie ensuite le document XML source.</span><span class="sxs-lookup"><span data-stu-id="842a4-111">It then modifies the source XML document.</span></span> <span data-ttu-id="842a4-112">Il modifie l'attribut `CustomerID` sur le premier client.</span><span class="sxs-lookup"><span data-stu-id="842a4-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="842a4-113">Après la modification, les commandes feront référence à un client qui n'existe pas ; le document XML ne sera donc plus validé.</span><span class="sxs-lookup"><span data-stu-id="842a4-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="842a4-114">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="842a4-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="842a4-115">Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="842a4-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="842a4-116">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="842a4-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="842a4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="842a4-117">See Also</span></span>  
 <span data-ttu-id="842a4-118"><xref:System.Xml.Schema.Extensions.Validate%2A></span><span class="sxs-lookup"><span data-stu-id="842a4-118"><xref:System.Xml.Schema.Extensions.Validate%2A></span></span>   
 [<span data-ttu-id="842a4-119">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="842a4-119">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

