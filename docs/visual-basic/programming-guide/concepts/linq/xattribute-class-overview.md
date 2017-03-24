---
title: "Vue d’ensemble de la classe XAttribute (Visual Basic) | Documents Microsoft"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
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
ms.openlocfilehash: 1ce5f4be6006908b35057854f89432471fd9f06b
ms.lasthandoff: 03/13/2017

---
# <a name="xattribute-class-overview-visual-basic"></a>Vue d’ensemble de la classe XAttribute (Visual Basic)
Les attributs sont des paires nom/valeur associées à un élément. La <xref:System.Xml.Linq.XAttribute>classe représente des attributs XML.</xref:System.Xml.Linq.XAttribute>  
  
## <a name="overview"></a>Vue d'ensemble  
 L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] est semblable à l'utilisation des éléments. Leurs constructeurs sont similaires. Les méthodes que vous utilisez pour en récupérer des collections sont similaires. A [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] une expression de requête pour une collection d’attributs est très similaire à un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expression pour une collection d’éléments de requête.  
  
 L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé. Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.  
  
## <a name="the-xattribute-constructor"></a>Le constructeur XAttribute  
 Le constructeur suivant de la <xref:System.Xml.Linq.XAttribute>classe est celui que vous utiliserez couramment :</xref:System.Xml.Linq.XAttribute>  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Crée un <xref:System.Xml.Linq.XAttribute>objet.</xref:System.Xml.Linq.XAttribute> L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Création d'un élément avec un attribut  
 Le code suivant montre un élément qui contient un attribut à l’aide de littéraux XML en Visual Basic :  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Construction fonctionnelle d'attributs  
 Vous pouvez construire <xref:System.Xml.Linq.XAttribute>objets en ligne avec la construction de <xref:System.Xml.Linq.XElement>des objets, comme suit :</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>Les attributs ne sont pas des nœuds  
 Il existe certaines différences entre les attributs et les éléments. <xref:System.Xml.Linq.XAttribute>les objets ne sont pas des nœuds dans l’arborescence XML.</xref:System.Xml.Linq.XAttribute> Il s'agit de paires nom/valeur associées à un élément XML. Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML. Bien que <xref:System.Xml.Linq.XAttribute>objets ne sont pas réellement des nœuds dans l’arborescence XML, l’utilisation <xref:System.Xml.Linq.XAttribute>objets est très similaire à l’utilisation de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XAttribute>  
  
 Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud. De nombreux développeurs n'auront pas à se sourcier de cette distinction.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML programmation présentation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
