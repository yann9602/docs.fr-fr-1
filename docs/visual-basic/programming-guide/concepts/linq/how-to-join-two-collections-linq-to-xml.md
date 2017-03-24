---
title: "Comment : joindre deux Collections (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 169a2ca7fb7fdc7b4cccdaab6547c6bb1a66072c
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Comment : joindre deux Collections (LINQ to XML) (Visual Basic)
Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut. Par exemple, le [exemple de fichier XML : clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) document XML contient une liste de clients et une liste de commandes. Chaque élément `Customer` contient un attribut `CustomerID`. Chaque élément `Order` contient un élément `CustomerID`. L'élément `CustomerID` dans chaque commande fait référence à l'attribut `CustomerID` dans un client.  
  
 La rubrique [exemple de fichier XSD : clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contient un XSD qui peut être utilisé pour valider ce document. Il utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.  
  
 Avec [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez tirer parti de cette relation en utilisant la clause `Join`.  
  
 Notez que dans la mesure où aucun index n'est disponible, une telle jointure présentera de faibles performances à l'exécution.  
  
 Pour plus d’informations sur les `Join`, consultez [les opérations de jointures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant joint les éléments `Customer` aux éléments `Order` et génère un nouveau document XML qui inclut l'élément `CompanyName` dans les commandes.  
  
 Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma dans [exemple de fichier XSD : clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Cela permet de s'assurer que la clause de jointure fonctionnera toujours.  
  
 Cette requête récupère d'abord tous les éléments `Customer`, puis les joint aux éléments `Order`. Elle sélectionne uniquement les commandes pour les clients dont le `CustomerID` est supérieur à « K ». Elle projette ensuite un nouvel élément `Order` qui contient les informations relatives aux clients dans chaque commande.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Cet exemple utilise le schéma XSD suivant : [exemple de fichier XSD : clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Notez que les performances d'une telle jointure ne seront pas très bonnes. Les jointures sont effectuées par le biais d'une recherche linéaire. Il n'y a aucun index ou table de hachage pour améliorer les performances.  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 Ce code génère la sortie suivante :  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de requêtes (LINQ to XML) avancées (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
