---
title: "Comment : transformer la forme d’une arborescence XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c71f4af829a395204bc17161547aa5fdd06cbb1
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Comment : transformer la forme d’une arborescence XML (Visual Basic)
Le *forme* d’un document XML document fait référence à ses noms d’éléments, les noms d’attributs et les caractéristiques de sa hiérarchie.  
  
 Parfois, vous devrez modifier la forme d'un document XML. Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents. Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir. Pour plus d’informations sur la construction fonctionnelle, consultez [Construction fonctionnelle (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Le premier exemple modifie l'organisation du document XML. Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.  
  
 Le deuxième exemple de cette rubrique crée un document XML avec une forme différente de celle du document source. Il modifie la casse des noms d’éléments, renomme certains éléments et laisse certains éléments de l’arborescence source en dehors de l’arborescence transformée.  
  
## <a name="example"></a>Exemple  
 Le code suivant modifie la forme d'un fichier XML à l'aide d'expressions de requête incorporées.  
  
 Le document XML source dans cet exemple contient un élément `Customers` sous l'élément `Root` qui contient tous les clients. Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes. Cet exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un élément `Orders` dans un élément `Customer`. Le document d'origine contient également un élément `CustomerID` dans l'élément `Order` ; cet élément sera supprimé du document reformé.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
  
        <Root>  
<Customer CustomerID="GREAL">  
  <CompanyName>Great Lakes Food Market</CompanyName>  
  <ContactName>Howard Snyder</ContactName>  
  <ContactTitle>Marketing Manager</ContactTitle>  
  <Phone>(503) 555-7555</Phone>  
  <FullAddress>  
    <Address>2732 Baker Blvd.</Address>  
    <City>Eugene</City>  
    <Region>OR</Region>  
    <PostalCode>97403</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
. . .  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple renomme certains éléments et convertit certains attributs en éléments.  
  
 Le code appelle `ConvertAddress`, qui renvoie une liste de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Projections et Transformations (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
