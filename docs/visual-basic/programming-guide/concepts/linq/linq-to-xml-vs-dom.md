---
title: "LINQ to XML, différences par rapport à DOM (Visual Basic) | Documents Microsoft"
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
ms.assetid: 18c36130-d598-40b7-9007-828232252978
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
ms.openlocfilehash: 88b6bddcdeec2859844f5d5f94777146d488b5fb
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML, différences par rapport à DOM (Visual Basic)
Cette section décrit quelques différences clés entre [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et le XML dominante actuellement API de programmation, le W3C modèle DOM (Document Object).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nouvelles manières de construire des arborescences XML  
 Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.  
  
 Par exemple, ce qui suit est une manière classique pour créer une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument>:</xref:System.Xml.XmlDocument>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]prend en charge cette approche de construction d’une arborescence XML, mais également une autre approche, *construction fonctionnelle*. Dans Visual Basic, la construction fonctionnelle utilise des littéraux XML pour générer une arborescence XML.  
  
 Voici comment vous devez construire la même arborescence XML à l’aide de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] construction fonctionnelle :  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.  
  
 Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Utilisation directe des éléments XML  
 Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs. Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez utiliser directement les éléments et les attributs XML. Vous pouvez par exemple effectuer les opérations suivantes :  
  
-   Créer des éléments XML sans utiliser d'objet de document. Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.  
  
-   Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.  
  
-   Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.  
  
 Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML. Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML. Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]évite cette couche de complexité.  
  
 Lorsque vous utilisez LINQ to XML, vous utilisez la <xref:System.Xml.Linq.XDocument>classe uniquement si vous souhaitez ajouter un commentaire ou le traitement au niveau racine du document.</xref:System.Xml.Linq.XDocument>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Gestion simplifiée des noms et des espaces de noms  
 La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]simplifie les noms et les espaces de noms en éliminant la nécessité de gérer avec des préfixes d’espace de noms. Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms. Mais si vous décidez de ne sont pas explicitement contrôler les préfixes d’espace de noms, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] affectera des préfixes d’espace de noms lors de la sérialisation s’ils sont requis ou effectuera la sérialisation à l’aide des espaces de noms par défaut s’ils ne le sont pas. Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant. Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud. Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]évite ce problème en vous permettant de définir le <xref:System.Xml.Linq.XName>propriété sur un nœud.</xref:System.Xml.Linq.XName>  
  
## <a name="static-method-support-for-loading-xml"></a>Prise en charge des méthodes statiques pour le chargement de données XML  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]vous permet de charger XML à l’aide des méthodes statiques au lieu de méthodes d’instance. Cela simplifie le chargement et l'analyse. Pour plus d’informations, consultez [Comment : chargement de XML à partir d’un fichier (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Suppression de la prise en charge des constructions de DTD  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités. La gestion des entités est complexe et rarement utilisée. La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation. Lorsqu’un [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] arborescence est remplie, toutes les entités DTD sont développées.  
  
## <a name="support-for-fragments"></a>Prise en charge des fragments  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]ne fournit pas d’équivalent pour la `XmlDocumentFragment` classe. Dans de nombreux cas, toutefois, le `XmlDocumentFragment` concept peut être géré par le résultat d’une requête typée comme <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XNode>, ou <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XNode> </xref:System.Collections.Generic.IEnumerable%601>  
  
## <a name="support-for-xpathnavigator"></a>Prise en charge de XPathNavigator  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Fournit la prise en charge de <xref:System.Xml.XPath.XPathNavigator>via les méthodes d’extension dans le <xref:System.Xml.XPath?displayProperty=fullName>espace de noms.</xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.XPath.XPathNavigator> Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</xref:System.Xml.XPath.Extensions?displayProperty=fullName>  
  
## <a name="support-for-white-space-and-indentation"></a>Prise en charge des espaces blancs et de la mise en retrait  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]gère les espaces blancs plus simplement que le modèle DOM.  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]stocke un espace blanc comme un <xref:System.Xml.Linq.XText>nœud, au lieu d’avoir spécialisé <xref:System.Xml.XmlNodeType>type de nœud, comme le modèle DOM procède.</xref:System.Xml.XmlNodeType> </xref:System.Xml.Linq.XText>  
  
## <a name="support-for-annotations"></a>Prise en charge des annotations  
 Les éléments [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] prennent en charge un ensemble extensible d'annotations. Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications. Pour plus d’informations, consultez [Annotations LINQ to XML](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Prise en charge des informations de schéma  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Fournit la prise en charge de la validation XSD via les méthodes d’extension dans le <xref:System.Xml.Schema?displayProperty=fullName>espace de noms.</xref:System.Xml.Schema?displayProperty=fullName> Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD. Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset). Pour plus d’informations, consultez [Comment : valider le XSD à l’aide de](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) et <xref:System.Xml.Schema.Extensions>.</xref:System.Xml.Schema.Extensions>  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
